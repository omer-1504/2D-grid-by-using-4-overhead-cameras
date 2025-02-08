# 2D-grid-by-using-4-overhead-cameras
The project aims to create a system that captures images from multiple cameras in a 3D room, stitches these images into a seamless panoramic view, and converts the stitched image into a 2D grid map. This grid map will represent object positions and dimensions, enabling efficient robot navigation and obstacle avoidance.

## Problem Statement

Develop a 2D Occupancy Grid Map of a Room using four Overhead Cameras

## Solution

## Multi-Camera Setup:

Install and calibrate four cameras in the room to capture different perspectives without overlapping views.
## Image Capture:

Capture images simultaneously from all four cameras.
## Image Stitching:

- **Preprocessing:** Resize, normalize, and convert images to grayscale.
- **Feature Detection:** Use SIFT/ORB algorithms to detect key features in the images.
- **Feature Matching:** Match features across images using FLANN.
-**Homography Estimation:** Use RANSAC to estimate homography and align images.
-**Image Blending:** Blend the aligned images into a seamless panoramic view.
## 2D Grid Mapping:

Convert the stitched image into a 2D grid map.
Represent objects in the room as lines or dots on the grid based on their dimensions.
## Navigation and Obstacle Detection:

- **Distance Calculation:** Calculate distances between various points on the grid.
- **Path Planning:** Use algorithms like Dijkstra’s or A* to plan optimal paths and avoid obstacles.
## Performance Evaluation:

Measure the accuracy of the grid map and computational latency to ensure real-time performance.

## Tech Stack

## Hardware:

- **Cameras:** High-resolution cameras capable of capturing clear images from different angles.
- **Computing Device:** A powerful computer or server with sufficient processing power and memory.

## Software:

- **Operating System:** Ubuntu or any other Linux distribution for robust performance and compatibility with simulation and vision libraries.
- **Gazebo:** For simulating the environment and camera setup.
- **ROS (Robot Operating System):** For integrating different components and managing communication between them.
- **OpenCV:** For image processing tasks such as resizing, normalization, feature detection, and stitching.
- **Python/C++:** For writing scripts and algorithms for image processing, stitching, and grid mapping.
- **Pandas/Numpy:** For data manipulation and handling large datasets efficiently.
- **SciPy:** For scientific computations, including optimization algorithms used in stitching and mapping.

## Team Members

- **Nadupalli Roja Ashritha**: Team Lead and web developer
- **Vemula Ranjith**: web developer
- **Syed Omer Farooq**: backend developer

## Contact Information

For any questions or feedback, feel free to reach out to us:

- **Nadupalli Roja Ashritha**: [21311a6614@sreenidhi.edu.in](mailto:21311a6614@sreenidhi.edu.in)
- **Vemula Ranjith**: [21311a6615@sreenidhi.edu.in](mailto:21311a6615@sreenidhi.edu.in)
- **Syed Omer Farooq**: [21311a6616@sreenidhi.edu.in](mailto:2311a6616@sreenidhi.edu.in)

## Acknowledgements

We would like to thank Intel Unnati for providing us with this opportunity to innovate and create. Special thanks to our mentors and everyone who supported us in this project.

---

**Develop 2D grid by using four Overhead Cameras** - Innovation Nexus
