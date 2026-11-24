# Opening and Closing Operations Using OpenCV

## Aim

To write a Python program using OpenCV to perform morphological Opening and Closing operations on an image.

The program performs the following operations:

- Morphological Opening
- Morphological Closing

## Software Used

- Anaconda – Python 3.7
- Jupyter Notebook / VS Code
- OpenCV (cv2)
- NumPy
- Matplotlib

## Algorithm

### Step 1:

Import the required libraries: OpenCV, NumPy, and Matplotlib.

### Step 2:

Create or load an input image containing foreground objects.

### Step 3:

Display the original image.

### Step 4:

Create a structuring element (kernel) of suitable size.

### Step 5: Opening Operation

- Apply the Opening operation using the structuring element.
- Opening consists of Erosion followed by Dilation.
- Remove small foreground noises while preserving the shape of larger objects.
- Display the opened image.

### Step 6: Closing Operation

- Apply the Closing operation using the structuring element.
- Closing consists of Dilation followed by Erosion.
- Fill small holes and gaps within foreground objects.
- Display the closed image.

### Step 7:

Compare the original, opened, and closed images.

## Program

## Developed By
# Name: Vijiyalakshmi A
# Register No: 212225240185

```p
import cv2
import numpy as np
import matplotlib.pyplot as plt

# Read input image
img = cv2.imread('butterfly.jpg')

if img is None:
    print("Image not found!")

else:
    # Create a larger kernel
    kernel = np.ones((21, 21), np.uint8)

    # Opening operation
    opening = cv2.morphologyEx(img, cv2.MORPH_OPEN, kernel)

    # Closing operation
    closing = cv2.morphologyEx(img, cv2.MORPH_CLOSE, kernel)

    # Calculate differences
    diff_open = cv2.absdiff(img, opening)
    diff_close = cv2.absdiff(img, closing)

    # Enhance differences for visibility
    diff_open = cv2.convertScaleAbs(diff_open, alpha=4)
    diff_close = cv2.convertScaleAbs(diff_close, alpha=4)

    # Display results
    plt.figure(figsize=(15, 10))

    plt.subplot(2, 2, 1)
    plt.imshow(cv2.cvtColor(img, cv2.COLOR_BGR2RGB))
    plt.title("Original Image")
    plt.axis('off')

    plt.subplot(2, 2, 2)
    plt.imshow(cv2.cvtColor(opening, cv2.COLOR_BGR2RGB))
    plt.title("Opening Operation")
    plt.axis('off')

    plt.subplot(2, 2, 3)
    plt.imshow(cv2.cvtColor(closing, cv2.COLOR_BGR2RGB))
    plt.title("Closing Operation")
    plt.axis('off')
```

## Output

### Original Image

- The input image is displayed.
- The image serves as the source for morphological processing.

<img width="235" height="360" alt="image" src="https://github.com/user-attachments/assets/965b67e5-88ba-45c5-91df-4bdd9bc021da" />

### Opening Operation

- Original image is displayed.
- Opened image is displayed.
- Small foreground noise is removed.
- Thin protrusions and isolated pixels are eliminated.
- Object boundaries become smoother.

<img width="235" height="360" alt="image" src="https://github.com/user-attachments/assets/3331bac7-95b0-405c-a9ba-0e5bf608f56d" /><img width="241" height="362" alt="image" src="https://github.com/user-attachments/assets/628c5865-89a9-47ce-8d63-6cc05b856ce2" />


### Closing Operation

- Original image is displayed.
- Closed image is displayed.
- Small holes and gaps inside objects are filled.
- Broken regions are connected.
- Object boundaries become more continuous.

<img width="235" height="360" alt="image" src="https://github.com/user-attachments/assets/d62a6c4b-9482-4fa6-936d-ab98514230ad" /><img width="222" height="360" alt="image" src="https://github.com/user-attachments/assets/1a663509-fc14-4b1b-bb2e-a91c114f659a" />


## Applications

### Opening

- Noise removal in binary images.
- Separation of connected objects.
- Preprocessing for object detection.

### Closing

- Filling small holes in objects.
- Connecting nearby components.
- Enhancing segmented regions.

## Advantages

### Opening

- Removes unwanted foreground noise.
- Preserves major object structures.
- Improves segmentation quality.

### Closing

- Restores object continuity.
- Eliminates small background gaps.
- Improves object representation.

## Result

Thus, the morphological operations **Opening** and **Closing** are successfully implemented using OpenCV. 
