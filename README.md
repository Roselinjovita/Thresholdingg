# THRESHOLDING
## Aim
To segment the image using global thresholding, adaptive thresholding and Otsu's thresholding using python and OpenCV.

## Software Required
1. Anaconda - Python 3.7
2. OpenCV

## Algorithm

### Step1:
Load the input image using cv2.imread() and convert it to a grayscale image using cv2.cvtColor() with the color conversion code cv2.COLOR_BGR2GRAY.

### Step2:
Use a fixed threshold value (e.g., 127) for global thresholding with cv2.threshold(). Pixels with intensity above this value are set to maximum intensity (255), and the rest are set to minimum intensity (0).

### Step3:
Use adaptive thresholding, which calculates the threshold for smaller regions of the image. The threshold is calculated dynamically using cv2.adaptiveThreshold() with the ADAPTIVE_THRESH_GAUSSIAN_C method.

### Step4:
Otsu's method automatically finds an optimal threshold value by minimizing the within-class variance. Apply it using cv2.threshold() with the flag cv2.THRESH_OTSU.

### Step5:
Use plt.imshow() to visualize the grayscale image and the segmented images from global, adaptive, and Otsu's thresholding techniques.

## Program and Output

### Original Image
```python
# Load the necessary packages
import cv2
import matplotlib.pyplot as plt

# Read the Image and convert to grayscale
image = cv2.imread('minion.jpg')
gray_image = cv2.cvtColor(image, cv2.COLOR_BGR2GRAY)

plt.imshow(gray_image, cmap='gray')
plt.title('Grayscale Image')
plt.xticks([]), plt.yticks([])
plt.show()
```
![Screenshot 2024-10-26 104907](https://github.com/user-attachments/assets/138935cb-7f94-4481-884a-9291b27a4448)


### Global Thresholding

```python
# Use Global thresholding to segment the image
ret_global, th_global = cv2.threshold(gray_image, 127, 255, cv2.THRESH_BINARY)

# Display the global thresholding result
plt.imshow(th_global, cmap='gray')
plt.title('Global Thresholding (v=127)')
plt.xticks([]), plt.yticks([])
plt.show()
```

![Screenshot 2024-10-26 104917](https://github.com/user-attachments/assets/99d31064-3d82-42a7-94a0-b77039207867)



### Adaptive Thresholding
```python
# Use Adaptive thresholding to segment the image
thresh_adaptive = cv2.adaptiveThreshold(gray_image, 255, cv2.ADAPTIVE_THRESH_GAUSSIAN_C,cv2.THRESH_BINARY, 11, 2)

# Display the adaptive thresholding result
plt.imshow(thresh_adaptive, cmap='gray')
plt.title('Adaptive Gaussian Thresholding')
plt.xticks([]), plt.yticks([])
plt.show()
```
![Screenshot 2024-10-26 104930](https://github.com/user-attachments/assets/f6969894-fde0-4f12-b34d-b2001b5a07cc)



### Optimum Global Thesholding using Otsu's Method
```python
# Use Otsu's method to segment the image 
ret_otsu, th_otsu = cv2.threshold(gray_image, 0, 255, cv2.THRESH_BINARY + cv2.THRESH_OTSU)

# Display the results
plt.imshow(th_otsu, cmap='gray')
plt.title("Otsu's Thresholding")
plt.xticks([]), plt.yticks([])
plt.show()
```

![Screenshot 2024-10-26 104951](https://github.com/user-attachments/assets/a98f2864-1bd8-416c-83bb-88e2fda68a09)


## Result
Thus the images are segmented using global thresholding, adaptive thresholding and optimum global thresholding using python and OpenCV.
