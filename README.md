import os
import cv2

# Specify the path to your sample dental image
sample_image_path = r"C:\Users\temar\Downloads\archive (2)\valid\0834_jpg.rf.5fd767b97b8d161100ce894254e5783f.jpg"

# Check if the file exists before attempting to load it
if os.path.isfile(sample_image_path):
    # Load the sample dental image
    sample_image = cv2.imread(sample_image_path)

    # Check if the image is loaded successfully
    if sample_image is None:
        print("Error: Unable to load the sample image.")
    else:
        # Preprocess the image and detect cavities (replace this with your actual cavity detection code)
        processed_image = cv2.cvtColor(sample_image, cv2.COLOR_BGR2GRAY)  # Example preprocessing (grayscale conversion)
        
        # Example cavity detection algorithm (marking cavities with red rectangles)
        detected_image = sample_image.copy()
        cv2.rectangle(detected_image, (100, 100), (200, 200), (0, 0, 255), 2)  # Example: Draw a red rectangle
        
        # Save the processed image with detected cavities
        cv2.imwrite("detected_cavities_image.jpg", detected_image)
        
        # Display the processed image for visualization (optional)
        cv2.imshow("Detected Cavities", detected_image)
        cv2.waitKey(0)
        cv2.destroyAllWindows()
else:
    print(f"Error: The file {sample_image_path} does not exist.")
