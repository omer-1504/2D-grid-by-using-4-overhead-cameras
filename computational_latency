import time
import numpy as np
import cv2

def process_and_composite_images(images):
    processed_images = [cv2.resize(image, (640, 480)) for image in images]
    composite_map = np.vstack(processed_images)  # Example composite operation
    return composite_map

def generate_dummy_images(num_images=4, image_size=(640, 480)):
    return [np.random.randint(0, 256, image_size, dtype=np.uint8) for _ in range(num_images)]

def measure_latency():
    images = generate_dummy_images()
    start_time = time.time()
    composite_map = process_and_composite_images(images)
    end_time = time.time()
    latency = (end_time - start_time) * 1000  # Convert to milliseconds
    return latency

latency = measure_latency()
print(f"Computing Latency: {latency} milliseconds")

if latency < 1000:
    print("The computational latency is within the acceptable range (< 1000ms).")
else:
    print("The computational latency exceeds the acceptable range (>= 1000ms).")
