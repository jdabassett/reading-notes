# **Reading Notes: OpenCV**

---
---
---

## Why are these reading important?

```
```

---

## [**OpenCV Examples:**](https://www.kaggle.com/code/bulentsiyah/learn-opencv-by-examples-with-python)

#### [**Image Sharpening:**](https://www.kaggle.com/code/bulentsiyah/learn-opencv-by-examples-with-python?scriptVersionId=34321869&cellId=4)

* WHY?
* ChatGPT: Sharpening images with OpenCV or any other image processing library is a technique used to enhance the edges and details in an image. It is often employed to improve the visual quality of images and make them appear clearer and more defined. 

```python
# import image
image = cv2.imread('/path.jpg')

# convert to usagable version, rgb
image = cv2.cvtColor(image, cv2.COLOR_BGR2RGB)

# create figure
plt.figure(figsize=(20, 20))
# add current image
plt.subplot(1, 2, 1)
plt.title("Original")
plt.imshow(image)


# create kernel to apply as filter
# won't normalize since values sum to 1
kernel_sharpening = np.array([[-1,-1,-1], 
                              [-1,9,-1], 
                              [-1,-1,-1]])

# applying different kernels to the input image
sharpened = cv2.filter2D(image, -1, kernel_sharpening)

# add new image to figure
plt.subplot(1, 2, 2)
plt.title("Image Sharpening")
plt.imshow(sharpened)

# display figure
plt.show()
```

#### [**Thresholding:**](https://www.kaggle.com/code/bulentsiyah/learn-opencv-by-examples-with-python?scriptVersionId=34321869&cellId=7)

* WHY?
* ChatGPT:  To separate regions of interest in an image from the background or to highlight certain features.

```python
# load image as grayscale
image = cv2.imread('/path.jpg', 0)

# create figure
plt.figure(figsize=(30, 30))
# add current image
plt.subplot(3, 2, 1)
plt.title("Original")
plt.imshow(image)

# what, threshold is set by user and fixed
# Values below 127 goes to 0 (black, everything above goes to 255 (white)
# returns tuple of threshold and new image
ret,thresh1 = cv2.threshold(image, 127, 255, cv2.THRESH_BINARY)

# add new image to figure
plt.subplot(3, 2, 2)
plt.title("Threshold Binary")
plt.imshow(thresh1)


# what, blur image to reduce noise
# (3,3), larger kernel correlates to more blur
# 0, std of gaussian distribution
image = cv2.GaussianBlur(image, (3, 3), 0)

# what, variable threshold applied by pixel's local region
# 255, max value that can be assigned
# ADAPTIVE_THRESH_MEAN_C, method used
# THRESH_BINARY, type of threshold to be applied
# 3, size of local region
# 5, constant subtracted from calculated mean
thresh = cv2.adaptiveThreshold(image, 255, cv2.ADAPTIVE_THRESH_MEAN_C, cv2.THRESH_BINARY, 3, 5) 

# add new image to figure
plt.subplot(3, 2, 3)
plt.title("Adaptive Mean Thresholding")
plt.imshow(thresh)

# 0, threshold value but OTSU calc optimal from image histogram
# 255, max intensity to assign
# BINARY + OTSU, techniques applied
# BINARY, above set to 255, below set to 0
# OTSU, threshold method to determine threshold
# returns threshold value and new image
_, th2 = cv2.threshold(image, 0, 255, cv2.THRESH_BINARY + cv2.THRESH_OTSU)

# add image to figure
plt.subplot(3, 2, 4)
plt.title("Otsu's Thresholding")
plt.imshow(th2)


plt.subplot(3, 2, 5)

# see above
blur = cv2.GaussianBlur(image, (5,5), 0)
# see above, to demonstrate effect of blur
_, th3 = cv2.threshold(blur, 0, 255, cv2.THRESH_BINARY + cv2.THRESH_OTSU)

plt.title("Guassian Otsu's Thresholding")
plt.imshow(th3)

# show figure
plt.show()
```

---

#### [**:**]()

* WHY?
* ChatGPT:  

```python
```

---

#### [**:**]()

* WHY?
* ChatGPT:  

```python
```

---

## **Reading Questions:**

1. 

```
```

1. 

```
```

1. 

```
```

---

## **What I want to learn more about:**

1. 

---
---
---