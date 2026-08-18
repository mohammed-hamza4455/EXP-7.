# Detecting Lines Using Hough Transform

## Date: 17/08/2026

## Developed By

* **Name:** MOHAMMED HAMZA M
* **Register No:** 212224230167
* 
## Aim

To implement a basic line detection pipeline using OpenCV by detecting straight lines in an image using the Probabilistic Hough Transform.

---

## Learning Objective

* Understand the basic stages of image processing.
* Learn how to convert a color image into grayscale.
* Understand edge detection using the Canny algorithm.
* Learn how the Hough Transform is used for line detection.
* Practice detecting and highlighting lines using OpenCV.

---

## Software Used

* Anaconda – Python 3.7
* Jupyter Notebook / VS Code
* OpenCV (cv2)
* NumPy
* Matplotlib

---

## Algorithm & Explanation

---

### Step 1: Import Libraries

```python
import cv2
import numpy as np
import matplotlib.pyplot as plt
```

---

### Step 2: Read the Image

```python
# Read the image using OpenCV

image = cv2.imread('  hamza.jpg')
```

### Output

**Original Image:**

<img width="818" height="517" alt="image" src="https://github.com/user-attachments/assets/f94b81b2-d5f0-446f-bb95-b00820b5fb8b" />


---

### Step 3: Convert to Grayscale

```python
# Convert the image to grayscale

gray_image = cv2.cvtColor(image, cv2.COLOR_BGR2GRAY)
```

The original image is converted from the BGR color format into a grayscale image using `cv2.cvtColor()`.

Grayscale conversion simplifies the image and prepares it for edge detection.

### Output

**Grayscale Image:**

<img width="856" height="505" alt="image" src="https://github.com/user-attachments/assets/ee9877f5-c402-4948-8bd4-daed63d753ea" />


---

### Step 4: Edge Detection Using Canny

```python
# Perform Edge Detection

edges = cv2.Canny(gray_image, 50, 150, apertureSize=3)
```

The Canny edge detection algorithm is applied to the grayscale image.

The lower threshold is set to `50` and the upper threshold is set to `150`. The resulting image contains the detected edges.

### Output

**Canny Edge Detection Output:**

<img width="953" height="390" alt="image" src="https://github.com/user-attachments/assets/112e47e5-b7c9-4cb0-90e5-059cf49b95d0" />


---

### Step 5: Detect Lines Using Probabilistic Hough Transform

```python
# Detect lines using the probabilistic Hough transform

lines = cv2.HoughLinesP(
    edges,
    rho=1,
    theta=np.pi/180,
    threshold=100,
    minLineLength=50,
    maxLineGap=10
)
```

The Probabilistic Hough Transform is used to detect straight lines from the edge image.

The parameters used are:

* `rho=1` – distance resolution of the accumulator in pixels.
* `theta=np.pi/180` – angular resolution of 1 degree.
* `threshold=100` – minimum number of votes required for a line to be detected.
* `minLineLength=50` – minimum length of a detected line.
* `maxLineGap=10` – maximum gap between line segments that can be joined into a single line.


---

### Step 6: Draw the Detected Lines

```python
# Draw the lines on the original image

output_image = image.copy()

if lines is not None:
    for line in lines:
        x1, y1, x2, y2 = line
        cv2.line(output_image, (x1, y1), (x2, y2), (0, 255, 0), 2)
```

A copy of the original image is created using `image.copy()`.

If lines are detected, the coordinates of each line are extracted and the lines are drawn on the original image using `cv2.line()`.

The detected lines are displayed in green with a thickness of `2`.

### Output

**Final Line Detection Output:**

<img width="1076" height="522" alt="image" src="https://github.com/user-attachments/assets/a11f7e19-5a6f-4eb3-977b-cb274a38f626" />


---


## Result

Thus, the line detection pipeline is successfully implemented using OpenCV and the Probabilistic Hough Transform. The system detects straight lines from the edges of the input image and highlights the detected lines on the original image.

---
