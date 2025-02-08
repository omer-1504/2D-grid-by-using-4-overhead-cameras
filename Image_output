import rclpy
from rclpy.node import Node
from sensor_msgs.msg import Image
from cv_bridge import CvBridge
import cv2

class ImageListener(Node):

    def init(self):
        super().init('image_listener')
        self.subscription = self.create_subscription(
            Image,
            '/overhead_camera/overhead_camera1/image_raw',
            self.listener_callback,
            10)
        self.bridge = CvBridge()
        self.subscription = self.create_subscription(
            Image,
            '/overhead_camera/overhead_camera2/image_raw',
            self.listener_callback2,
            10)
        self.subscription = self.create_subscription(
            Image,
            '/overhead_camera/overhead_camera3/image_raw',
            self.listener_callback3,
            10)
        self.subscription = self.create_subscription(
            Image,
            '/overhead_camera/overhead_camera4/image_raw',
            self.listener_callback4,
            10)

    def listener_callback(self, msg):
        self.get_logger().info('Receiving image')
        cv_image = self.bridge.imgmsg_to_cv2(msg, 'bgr8')
        print('Dimensions of Image',cv_image.shape[0],cv_image.shape[1])
        cv2.imshow("Camera Image", cv_image)
        cv2.waitKey(1)
    def listener_callback2(self, msg):
        self.get_logger().info('Receiving image')
        cv_image = self.bridge.imgmsg_to_cv2(msg, 'bgr8')
        print('Dimensions of Image',cv_image.shape[0],cv_image.shape[1])
        cv2.imshow("Camera Image 2", cv_image)
        cv2.waitKey(1)
    def listener_callback3(self, msg):
        self.get_logger().info('Receiving image')
        cv_image = self.bridge.imgmsg_to_cv2(msg, 'bgr8')
        print('Dimensions of Image',cv_image.shape[0],cv_image.shape[1])
        cv2.imshow("Camera Image 3", cv_image)
        cv2.waitKey(1)
    def listener_callback4(self, msg):
        self.get_logger().info('Receiving image')
        cv_image = self.bridge.imgmsg_to_cv2(msg, 'bgr8')
        print('Dimensions of Image',cv_image.shape[0],cv_image.shape[1])
        cv2.imshow("Camera Image 4", cv_image)
        cv2.waitKey(1)

def main(args=None):
    rclpy.init(args=args)
    node = ImageListener()
    rclpy.spin(node)
    node.destroy_node()
    rclpy.shutdown()

if name == 'main':
    main()
