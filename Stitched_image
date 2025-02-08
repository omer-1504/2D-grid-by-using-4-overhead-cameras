import rclpy
from rclpy.node import Node
from sensor_msgs.msg import Image
from cv_bridge import CvBridge
import cv2
import numpy as np
import matplotlib.pyplot as plt

class ImageListener(Node):

    def init(self):
        super().init('image_listener')
        
        self.bridge = CvBridge()
        self.image1 = None
        self.image2 = None
        self.image3 = None
        self.image4 = None

        self.subscription1 = self.create_subscription(
            Image,
            '/overhead_camera/overhead_camera1/image_raw',
            self.listener_callback1,
            10)
        
        self.subscription2 = self.create_subscription(
            Image,
            '/overhead_camera/overhead_camera2/image_raw',
            self.listener_callback2,
            10)

        self.subscription3 = self.create_subscription(
            Image,
            '/overhead_camera/overhead_camera3/image_raw',
            self.listener_callback3,
            10)

        self.subscription4 = self.create_subscription(
            Image,
            '/overhead_camera/overhead_camera4/image_raw',
            self.listener_callback4,
            10)

    def listener_callback1(self, msg):
        self.get_logger().info('Receiving image 1')
        self.image1 = self.bridge.imgmsg_to_cv2(msg, 'bgr8')
        self.check_and_stitch()

    def listener_callback2(self, msg):
        self.get_logger().info('Receiving image 2')
        self.image2 = self.bridge.imgmsg_to_cv2(msg, 'bgr8')
        self.check_and_stitch()

    def listener_callback3(self, msg):
        self.get_logger().info('Receiving image 3')
        self.image3 = self.bridge.imgmsg_to_cv2(msg, 'bgr8')
        self.check_and_stitch()

    def listener_callback4(self, msg):
        self.get_logger().info('Receiving image 4')
        self.image4 = self.bridge.imgmsg_to_cv2(msg, 'bgr8')
        self.check_and_stitch()

    def check_and_stitch(self):
        if self.image1 is not None and self.image2 is not None and self.image3 is not None and self.image4 is not None:
            stitched_image = self.stitch_images([self.image1, self.image2, self.image3, self.image4])
            occupancy_grid = self.create_occupancy_grid(stitched_image)
            if occupancy_grid is not None:
                plt.imshow(occupancy_grid, cmap='gray')  # Display as grayscale occupancy grid
                plt.axis('off')
                plt.show()

    def stitch_images(self, images):
        height, width = images[0].shape[:2]
        resized_images = [cv2.resize(img, (width, height)) for img in images]
        canvas = np.zeros((height * 2, width * 2, 3), dtype=np.uint8)
        canvas[:height, :width] = resized_images[3]  # Top-left
        canvas[:height, width:] = resized_images[2]  # Top-right
        canvas[height:, :width] = resized_images[1]  # Bottom-left
        canvas[height:, width:] = resized_images[0]  # Bottom-right
        return canvas

    def create_occupancy_grid(self, stitched_image):
        gray_image = cv2.cvtColor(stitched_image, cv2.COLOR_BGR2GRAY)
        _, occupancy_grid = cv2.threshold(gray_image, 127, 255, cv2.THRESH_BINARY)
        return occupancy_grid


def main(args=None):
    rclpy.init(args=args)
    node = ImageListener()
    rclpy.spin(node)
    node.destroy_node()
    rclpy.shutdown()

if name == 'main':
    main()
