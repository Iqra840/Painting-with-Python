# Painting-with-Python
A program that converts an image into an oil painting using image processing. Using OpenCV, the program first performs 
import cv2
import numpy as np
import imageio
import matplotlib.pyplot as plt
from PIL import Image
# load image
im1 = imageio.imread(‘img.jpg’)
plt.imshow(im1)
plt.show()
img = cv2.imread("img.jpg")

# smoothing outline using morphology open
kernel = cv2.getStructuringElement(cv2.MORPH_ELLIPSE, (6,6))
morph = cv2.morphologyEx(img, cv2.MORPH_OPEN, kernel)

# normalizing to brighten darkerregions
result = cv2.normalize(morph,None,20,255,cv2.NORM_MINMAX)

# write result to disk
cv2.imwrite("windmill_oilpaint.jpg", result)

cv2.imshow("IMAGE", img)
cv2.imshow("OPEN", morph)
cv2.imshow("RESULT", result)
cv2.waitKey(0)
cv2.destroyAllWindows()