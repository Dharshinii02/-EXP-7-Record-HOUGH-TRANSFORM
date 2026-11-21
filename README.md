# -EXP-7-Record-HOUGH-TRANSFORM


**NAME:** Dharshini J  
**REG NO:** 212224240036

## Aim

To detect straight lines in an image using the Hough Transform technique with the Probabilistic Hough Line Transform function (`HoughLinesP()`) using Python and OpenCV.

## Software Required

1. Anaconda – Python 3.7
2. OpenCV
3. NumPy
4. Matplotlib

## Algorithm

### Step 1:
Read the input image using `cv2.imread()` from the OpenCV library.

### Step 2:
Convert the input image into a grayscale image using `cv2.cvtColor()`.

### Step 3:
Apply the Canny edge detection technique to detect the edges in the grayscale image.

### Step 4:
Apply the Probabilistic Hough Transform using `cv2.HoughLinesP()` to detect straight lines in the edge image.

### Step 5:
Use a `for` loop to extract the coordinates of the detected lines and draw them on the original image using `cv2.line()`.

### Step 6:
Display the original image, grayscale image, Canny edge image, and the final image with detected lines.

## Program

```
python
import cv2
import numpy as np
import matplotlib.pyplot as plt

# Read the input image
image = cv2.imread('image.jpeg')

# Convert the image to grayscale
gray_image = cv2.cvtColor(image, cv2.COLOR_BGR2GRAY)

# Display the input image
plt.imshow(cv2.cvtColor(image, cv2.COLOR_BGR2RGB))
plt.title("Input Image")
plt.axis('off')
plt.show()

# Display the grayscale image
plt.imshow(gray_image, cmap='gray')
plt.title("Grayscale Image")
plt.axis('off')
plt.show()

# Detect edges using Canny operator
edges = cv2.Canny(gray_image, 50, 150)

# Display the Canny edge detector output
plt.imshow(edges, cmap='gray')
plt.title("Canny Edge Detector")
plt.axis('off')
plt.show()

# Apply Probabilistic Hough Transform
lines = cv2.HoughLinesP(
    edges,
    1,
    np.pi / 180,
    100,
    minLineLength=50,
    maxLineGap=10
)

# Draw the detected lines on the original image
if lines is not None:
    for line in lines:
        x1, y1, x2, y2 = line[0]
        cv2.line(image, (x1, y1), (x2, y2), (0, 255, 0), 2)

# Display the result of Hough Transform
plt.imshow(cv2.cvtColor(image, cv2.COLOR_BGR2RGB))
plt.title("Result of Hough Transform")
plt.axis('off')
plt.show()
```

## Output

## 1. Input Image
<img width="316" height="402" alt="image" src="https://github.com/user-attachments/assets/98b94976-50ed-4d96-9810-77bf1e8fe387" />

## 2. Grayscale Image
<img width="310" height="415" alt="image" src="https://github.com/user-attachments/assets/7e4c0502-cd5b-4f88-aa28-218e5c1758c5" />

## 3. Canny Edge Detector
<img width="343" height="417" alt="image" src="https://github.com/user-attachments/assets/5955569a-2a75-4826-a4e9-98e65fc45c5f" />

## 4. Result of Hough Transform (Image with detected lines)
<img width="317" height="411" alt="image" src="https://github.com/user-attachments/assets/6ef66afe-64f3-4102-a902-f18cf67fc526" />

## Result

Thus, the straight lines in the input image are detected using the Probabilistic Hough Transform (`HoughLinesP()`) with Python and OpenCV.
