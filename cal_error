import numpy as np

def calculate_errors(infra_cam_distances, gazebo_distances):
    errors = np.abs(np.array(infra_cam_distances) - np.array(gazebo_distances))
    return errors
  
def compute_accuracy_metrics(errors, actual_distances):
    avg_error = np.mean(errors)
    min_error = np.min(errors)
    max_error = np.max(errors)
    avg_error_percentage = (avg_error / np.mean(actual_distances)) * 100
    return avg_error, min_error, max_error, avg_error_percentage
  
infra_cam_distances = [2.15, 4.61, 5.6]  # Example distances in meters
gazebo_distances = [2.43, 5.08, 6.15]  # Example ground truth distances in meters

errors = calculate_errors(infra_cam_distances, gazebo_distances)
print(f"Errors: {errors} meters")

avg_error, min_error, max_error, avg_error_percentage = compute_accuracy_metrics(errors, gazebo_distances)
print(f"Average Error: {avg_error} meters")
print(f"Minimum Error: {min_error} meters")
print(f"Maximum Error: {max_error} meters")
print(f"Average Error Percentage: {avg_error_percentage}%")

if avg_error_percentage < 10:
    print("The average error is within the acceptable range (< 10%).")
else:
    print("The average error is greater than the acceptable range (>= 10%).")
