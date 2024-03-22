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

#### [**Dilation, Erosion, Opening and Closing:**](https://www.kaggle.com/code/bulentsiyah/learn-opencv-by-examples-with-python?scriptVersionId=34321869&cellId=8)

* WHY?
* ChatGPT: Two fundamental morphological operations used to manipulate images based on the shapes contained within them. 

```python
image = cv2.imread('/kaggle/input/opencv-samples-images/data/LinuxLogo.jpg')
image = cv2.cvtColor(image, cv2.COLOR_BGR2RGB)

plt.figure(figsize=(20, 20))
plt.subplot(3, 2, 1)
plt.title("Original")
plt.imshow(image)


# declare kernel, think of them as weights for how surrounding pixels should impact the reassignment of the current pixel
kernel = np.ones((5,5), np.uint8)

# metaphor, think of an island surrounded by a rising sea
# result, fewer lagoons, decreases object size
erosion = cv2.erode(image, kernel, iterations = 1)

plt.subplot(3, 2, 2)
plt.title("Erosion")
plt.imshow(erosion)

# metaphor, think of an island in an upwell of the earths crust
# result, more island features, increses object size
dilation = cv2.dilate(image, kernel, iterations = 1)
plt.subplot(3, 2, 3)
plt.title("Dilation")
plt.imshow(dilation)


# opening, erosion followed by dilation
# result, smooths boundaries while maintaining size
opening = cv2.morphologyEx(image, cv2.MORPH_OPEN, kernel)
plt.subplot(3, 2, 4)
plt.title("Opening")
plt.imshow(opening)


# closing, dilation followed by erosion
# result, close small holes or games while maintaining
closing = cv2.morphologyEx(image, cv2.MORPH_CLOSE, kernel)
plt.subplot(3, 2, 5)
plt.title("Closing")
plt.imshow(closing)
```

---

#### [**Edge Detection and Image Gradients:**](https://www.kaggle.com/code/bulentsiyah/learn-opencv-by-examples-with-python?scriptVersionId=34321869&cellId=10)

* WHY?
* ChatGPT:  For feature detection, segmentation, and localization.

```python
image = cv2.imread('/path.jpg')
image = cv2.cvtColor(image, cv2.COLOR_BGR2RGB)

# declare height, width, and channels from image
height, width,_ = image.shape

# sorbel, edge detection
# first-order derivative measuring rate of change directly
# less sensitive to noise
# only x and/or y directions
# less computationally expensive

# CV_64F, depth of output image
# 0 and 1, specify direction
# ksize, size of kernel/ local region
# horizontally
sobel_x = cv2.Sobel(image, cv2.CV_64F, 0, 1, ksize=5)
# vertically
sobel_y = cv2.Sobel(image, cv2.CV_64F, 1, 0, ksize=5)

plt.figure(figsize=(20, 20))
plt.subplot(3, 2, 1)
plt.title("Original")
plt.imshow(image)
plt.subplot(3, 2, 2)
plt.title("Sobel X")
plt.imshow(sobel_x)
plt.subplot(3, 2, 3)
plt.title("Sobel Y")
plt.imshow(sobel_y)

# bitwise combine x and y
sobel_OR = cv2.bitwise_or(sobel_x, sobel_y)

plt.subplot(3, 2, 4)
plt.title("sobel_OR")
plt.imshow(sobel_OR)

# laplacia, edge detction
# second-order derivative measuring the rate of change
# more sensitive to noise, often paired with noise reduction
# isotropic, detecting edges from all directions
# more computationally expensive

# CV_64F, depth of output image
laplacian = cv2.Laplacian(image, cv2.CV_64F)

plt.subplot(3, 2, 5)
plt.title("Laplacian")
plt.imshow(laplacian)

# canny, edge detection
# multi-stage algorithm, highly regarded
# noise reduction, image gradients(sorbel), non-maximum suppression, and hysteresis thresholding
# allows for fine-tuning

# 50, lower threshold, below which edges won't be detected
# 120, upper threshold, any pixel above and already a good candidate is more heavily weighted as an edge
canny = cv2.Canny(image, 50, 120)

plt.subplot(3, 2, 6)
plt.title("Canny")
plt.imshow(canny)
```

---

#### [**Perpective Shift:**](https://www.kaggle.com/code/bulentsiyah/learn-opencv-by-examples-with-python?scriptVersionId=34321869&cellId=12)

* WHY?
* ChatGPT: Accomodate analysis from different viewpoints or perspectives. 

```python
image = cv2.imread('/path.jpg')
image = cv2.cvtColor(image, cv2.COLOR_BGR2RGB)

plt.figure(figsize=(20, 20))
plt.subplot(1, 2, 1)
plt.title("Original")
plt.imshow(image)

# matrix of points denoting top-left, top-right, bottom-left, and bottom-right
points_A = np.float32([[320,15], [700,215], [85,610], [530,780]])

# coordinates of the 4 corners of the desired output
points_B = np.float32([[0,0], [420,0], [0,594], [420,594]])
 
# Use the two sets of four points to compute 
# the Perspective Transformation matrix, M    
M = cv2.getPerspectiveTransform(points_A, points_B)
 
# what, perspective transformation on image
# M, transformation matrix mapping pixel inputs and outputs
# (420, 594), size of output
# return, new image
warped = cv2.warpPerspective(image, M, (420,594))

plt.subplot(1, 2, 2)
plt.title("warpPerspective")
plt.imshow(warped)
```

---

#### [**Scaling, resizing, and interpolations:**]()

* WHY?
* ChatGPT: To further processing.

```python
image = cv2.imread('/path.jpg')
image = cv2.cvtColor(image, cv2.COLOR_BGR2RGB)

plt.figure(figsize=(20, 20))
plt.subplot(2, 2, 1)
plt.title("Original")
plt.imshow(image)

# what, resize image to 75% 
# None, could specify output size instead
image_scaled = cv2.resize(image, None, fx=0.75, fy=0.75)

plt.subplot(2, 2, 2)
plt.title("Scaling - Linear Interpolation")
plt.imshow(image_scaled)

# what, resize image to 200%
# INTER_CUBIC, bicubic interpolation method
img_scaled = cv2.resize(image, None, fx=2, fy=2, interpolation = cv2.INTER_CUBIC)

plt.subplot(2, 2, 3)
plt.title("Scaling - Cubic Interpolation")
plt.imshow(img_scaled)

# (900,400), setting output size instead
# INTER_AREA, often for image downsizing
img_scaled = cv2.resize(image, (900, 400), interpolation = cv2.INTER_AREA)

plt.subplot(2, 2, 4)
plt.title("Scaling - Skewed Size")
plt.imshow(img_scaled)
```

---

#### [**Pyramid:**](https://www.kaggle.com/code/bulentsiyah/learn-opencv-by-examples-with-python?scriptVersionId=34321869&cellId=16)

* WHY?
* ChatGPT:  Image pyramids are multi-scale representations of an image typically generated by iteratively apply a series of actions to produce a heirarchy of images with progressively reduced resolution.

```python
image = cv2.imread('/path.jpg')
image = cv2.cvtColor(image, cv2.COLOR_BGR2RGB)

plt.figure(figsize=(20, 20))
plt.subplot(2, 2, 1)
plt.title("Original")
plt.imshow(image)

# what, gaussian pyramid construction and manipulation methods

# how, blur then downsampling to create lower resolution version
smaller = cv2.pyrDown(image)

# how, upsampling then blur to create a higher resolution version
larger = cv2.pyrUp(smaller)

plt.subplot(2, 2, 2)
plt.title("Smaller")
plt.imshow(smaller)

plt.subplot(2, 2, 3)
plt.title("Larger")
plt.imshow(larger)
```

---

#### [**Cropping:**](https://www.kaggle.com/code/bulentsiyah/learn-opencv-by-examples-with-python?scriptVersionId=34321869&cellId=18)

* WHY?
* ChatGPT:  Image processing.

```python
image = cv2.imread('/path.jpg')
image = cv2.cvtColor(image, cv2.COLOR_BGR2RGB)

plt.figure(figsize=(20, 20))
plt.subplot(2, 2, 1)
plt.title("Original")
plt.imshow(image)

# declare height and width from image shape
height, width = image.shape[:2]

# mutate and reassign
start_row, start_col = int(height * .25), int(width * .25)
end_row, end_col = int(height * .75), int(width * .75)

# slice or crop image
cropped = image[start_row:end_row , start_col:end_col]

plt.subplot(2, 2, 2)
plt.title("Cropped")
plt.imshow(cropped)
```

---

#### [**Blurring:**]()

* WHY?
* ChatGPT: Image processing to reduce noise or selectively reduce focus from areas of disinterest towards those of interest. 

```python
image = cv2.imread('/kaggle/path.jpg')
image = cv2.cvtColor(image, cv2.COLOR_BGR2RGB)

plt.figure(figsize=(20, 20))
plt.subplot(2, 2, 1)
plt.title("Original")
plt.imshow(image)

# declare kernel and normatize
# np.float32, specifies output data type
# /9, divides each element by 9, sum equal to 1
kernel_3x3 = np.ones((3, 3), np.float32) / 9

# kernel applied to image
# -1, specifies depth of output 
# larger kernels coorelate to more blur
blurred = cv2.filter2D(image, -1, kernel_3x3)

plt.subplot(2, 2, 2)
plt.title("3x3 Kernel Blurring")
plt.imshow(blurred)

# larger kernel
kernel_7x7 = np.ones((7, 7), np.float32) / 49
# more blur
blurred2 = cv2.filter2D(image, -1, kernel_7x7)

plt.subplot(2, 2, 3)
plt.title("7x7 Kernel Blurring")
plt.imshow(blurred2)
```

---

#### [**Contours:**](https://www.kaggle.com/code/bulentsiyah/learn-opencv-by-examples-with-python?scriptVersionId=34321869&cellId=22)

* WHY?
* ChatGPT: A list of points that represent the shape of an object in an image. Good for object detection, segmentation, shape analysis, measurement, and motion tracking

```python
# Let's load a simple image with 3 black squares
image = cv2.imread('/path.png')
image = cv2.cvtColor(image, cv2.COLOR_BGR2RGB)

plt.figure(figsize=(20, 20))
plt.subplot(2, 2, 1)
plt.title("Original")
plt.imshow(image)

# convet from BGR to grayscale
gray = cv2.cvtColor(image,cv2.COLOR_BGR2GRAY)

# canny, edge detection
# see above
# returns, binary image
edged = cv2.Canny(gray, 30, 200)

plt.subplot(2, 2, 2)
plt.title("Canny Edges")
plt.imshow(edged)

# what, find contours or the points that outline objects
# RETR_EXTERNAL, retrieval mode of contours, external/outer boundary of objects
# CHAIN_APPROX_NONE, stored in output contours list
# return, list of contours/points found and optional output to determine grouping and nesting
contours, hierarchy = cv2.findContours(edged, cv2.RETR_EXTERNAL, cv2.CHAIN_APPROX_NONE)

plt.subplot(2, 2, 3)
plt.title("Canny Edges After Contouring")
plt.imshow(edged)

print("Number of Contours found = " + str(len(contours)))

# what, draws contours on image
# -1, where to draw/store contours
# (0,255,0), color to draw/store them
# 3, pixel width
# in-place
cv2.drawContours(image, contours, -1, (0,255,0), 3)

plt.subplot(2, 2, 4)
plt.title("Contours")
plt.imshow(image)
```

---

#### [**Approximate Contours and Convex Hull:**](https://www.kaggle.com/code/bulentsiyah/learn-opencv-by-examples-with-python?scriptVersionId=34321869&cellId=24)

* WHY?
* ChatGPT: Convex hull is a polygon that encloses a set of points. Often representing the outermost contours of an image.

```python
image = cv2.imread('/path.jpg')
image = cv2.cvtColor(image, cv2.COLOR_BGR2RGB)

plt.figure(figsize=(20, 20))
plt.subplot(2, 2, 1)
plt.title("Original")
plt.imshow(image)

# make copy of image
orig_image = image.copy()

# convert to grayscale and segment through threshold
gray = cv2.cvtColor(image, cv2.COLOR_BGR2GRAY)
ret, thresh = cv2.threshold(gray, 127, 255, cv2.THRESH_BINARY_INV)

# find contours, see above
contours, hierarchy = cv2.findContours(thresh.copy(), cv2.RETR_LIST, cv2.CHAIN_APPROX_NONE)

# iterate through each contour and compute the bounding rectangle
for c in contours:
    # returns tuple of bounded rect for each object
    x,y,w,h = cv2.boundingRect(c)
    # draws rectangle on copy
    cv2.rectangle(orig_image,(x,y),(x+w,y+h),(0,0,255),2)

    plt.subplot(2, 2, 2)
    plt.title("Bounding Rectangle")
    plt.imshow(orig_image)

# halt execution until keyboard event, 0=indefinitely
cv2.waitKey(0) 
    
# iterate through each contour and compute the approx contour
for c in contours:
    # calculate accuracy as a percent of the contour perimeter(3%)
    accuracy = 0.03 * cv2.arcLength(c, True)
    # simplified polygon computed
    # approximate polygon douglas-peucker algorithm
    approx = cv2.approxPolyDP(c, accuracy, True)
    # draw to image
    cv2.drawContours(image, [approx], 0, (0, 255, 0), 2)
    
    plt.subplot(2, 2, 3)
    plt.title("Approx Poly DP")
    plt.imshow(image)

plt.show()
    
# Convex Hull
image = cv2.imread('/path.jpg')
gray = cv2.cvtColor(image, cv2.COLOR_BGR2GRAY)

plt.figure(figsize=(20, 20))
plt.subplot(1, 2, 1)
plt.title("Original Image")
plt.imshow(image)

ret, thresh = cv2.threshold(gray, 176, 255, 0)
contours, hierarchy = cv2.findContours(thresh.copy(), cv2.RETR_LIST, cv2.CHAIN_APPROX_NONE)
    
# sort contours by area and then remove the largest frame contour
n = len(contours) - 1
contours = sorted(contours, key=cv2.contourArea, reverse=False)[:n]

# Iterate through contours and draw the convex hull
for c in contours:
    # computes comvex hull
    # encloses the contour while being convex, no internal angles > 180deg
    hull = cv2.convexHull(c)
    # drawn onto image, in-place
    cv2.drawContours(image, [hull], 0, (0, 255, 0), 2)

    plt.subplot(1, 2, 2)
    plt.title("Convex Hull")
    plt.imshow(image)
```

---

#### [**Draw shapes and write text to images:**]

```python
image = cv2.imread('/path.jpg')
image = cv2.cvtColor(image, cv2.COLOR_BGR2RGB)
gray = cv2.cvtColor(image, cv2.COLOR_BGR2GRAY)

plt.figure(figsize=(20, 20))
plt.subplot(2, 2, 1)
plt.title("Original")
plt.imshow(image)

ret, thresh = cv2.threshold(gray, 127, 255, 1)
contours, hierarchy = cv2.findContours(thresh.copy(), cv2.RETR_LIST, cv2.CHAIN_APPROX_NONE)

for cnt in contours:
    # get approximate polygons
    approx = cv2.approxPolyDP(cnt, 0.01*cv2.arcLength(cnt,True),True)
    if len(approx) == 3:
        shape_name = "Triangle"
        cv2.drawContours(image,[cnt],0,(0,255,0),-1)
        # find contour center to place text at the center
        M = cv2.moments(cnt)
        cx = int(M['m10'] / M['m00'])
        cy = int(M['m01'] / M['m00'])
        cv2.putText(image, shape_name, (cx-50, cy), cv2.FONT_HERSHEY_SIMPLEX, 1, (0, 0, 0), 2)
    
    elif len(approx) == 4:
        x,y,w,h = cv2.boundingRect(cnt)
        M = cv2.moments(cnt)
        cx = int(M['m10'] / M['m00'])
        cy = int(M['m01'] / M['m00'])
        # check to see if 4-side polygon is square or rectangle
        # cv2.boundingRect returns the top left and then width and 
        if abs(w-h) <= 3:
            shape_name = "Square"
            # find contour center to place text at the center
            cv2.drawContours(image, [cnt], 0, (0, 125 ,255), -1)
            cv2.putText(image, shape_name, (cx-50, cy), cv2.FONT_HERSHEY_SIMPLEX, 1, (0, 0, 0), 2)
        else:
            shape_name = "Rectangle"
            # find contour center to place text at the center
            cv2.drawContours(image, [cnt], 0, (0, 0, 255), -1)
            M = cv2.moments(cnt)
            cx = int(M['m10'] / M['m00'])
            cy = int(M['m01'] / M['m00'])
            cv2.putText(image, shape_name, (cx-50, cy), cv2.FONT_HERSHEY_SIMPLEX, 1, (0, 0, 0), 2)
            
    elif len(approx) == 10:
        shape_name = "Star"
        cv2.drawContours(image, [cnt], 0, (255, 255, 0), -1)
        M = cv2.moments(cnt)
        cx = int(M['m10'] / M['m00'])
        cy = int(M['m01'] / M['m00'])
        cv2.putText(image, shape_name, (cx-50, cy), cv2.FONT_HERSHEY_SIMPLEX, 1, (0, 0, 0), 2)
        
    elif len(approx) >= 15:
        shape_name = "Circle"
        cv2.drawContours(image, [cnt], 0, (0, 255, 255), -1)
        M = cv2.moments(cnt)
        cx = int(M['m10'] / M['m00'])
        cy = int(M['m01'] / M['m00'])
        cv2.putText(image, shape_name, (cx-50, cy), cv2.FONT_HERSHEY_SIMPLEX, 1, (0, 0, 0), 2)

plt.subplot(2, 2, 2)
plt.title("Identifying Shapes")
plt.imshow(image)
```

---

#### [**Hough Lines:**](https://www.kaggle.com/code/bulentsiyah/learn-opencv-by-examples-with-python?scriptVersionId=34321869&cellId=28)

* WHY?
* ChatGPT: Hough lines is a technique to detect straight lines in an image. Efficient and good with noise

```python
image = cv2.imread('/path.png')
image = cv2.cvtColor(image, cv2.COLOR_BGR2RGB)
gray = cv2.cvtColor(image, cv2.COLOR_BGR2GRAY)
# see above
edges = cv2.Canny(gray, 100, 170, apertureSize = 3)

plt.figure(figsize=(20, 20))
plt.subplot(2, 2, 1)
plt.title("edges")
plt.imshow(edges)

# calculate HoughLines using a rho accuracy of 1 pixel
# theta accuracy of np.pi / 180 which is 1 degree
# threshold is set to 200points to make a line
lines = cv2.HoughLines(edges, 1, np.pi/180, 200)

# iterate through each line and convert it to the format
# required by cv.lines (i.e. requiring end points)
for line in lines:
    rho, theta = line[0]
    a = np.cos(theta)
    b = np.sin(theta)
    # point at origin
    x0 = a * rho
    y0 = b * rho
    # points at ends (outside range of image)
    # note they will be truncated when drawn
    x1 = int(x0 + 1000 * (-b))
    y1 = int(y0 + 1000 * (a))
    x2 = int(x0 - 1000 * (-b))
    y2 = int(y0 - 1000 * (a))
    # draws line to image
    # two points
    # color of line and thickness
    cv2.line(image, (x1, y1), (x2, y2), (255, 0, 0), 2)


plt.subplot(2, 2, 2)
plt.title("Hough Lines")
plt.imshow(image)
```

---

#### [**Counting Circles and Ellipses:**](https://www.kaggle.com/code/bulentsiyah/learn-opencv-by-examples-with-python?scriptVersionId=34321869&cellId=30)

```python
image = cv2.imread('/path.jpg')
image = cv2.cvtColor(image, cv2.COLOR_BGR2RGB)
plt.figure(figsize=(20, 20))

# intialize the detector using the default parameters
detector = cv2.SimpleBlobDetector_create()
# detect blobs
keypoints = detector.detect(image)
 
# draw blobs on image as red circles
blank = np.zeros((1,1)) 
blobs = cv2.drawKeypoints(image, keypoints, blank, (0,0,255), cv2.DRAW_MATCHES_FLAGS_DRAW_RICH_KEYPOINTS)

number_of_blobs = len(keypoints)
text = "Total Number of Blobs: " + str(len(keypoints))
cv2.putText(blobs, text, (20, 550), cv2.FONT_HERSHEY_SIMPLEX, 1, (100, 0, 255), 2)
plt.subplot(2, 2, 1)
plt.title("Blobs using default parameters")
plt.imshow(blobs)

# initialize parameter setting using cv2.SimpleBlobDetector
params = cv2.SimpleBlobDetector_Params()
# set Area filtering parameters
params.filterByArea = True
params.minArea = 100
# set Circularity filtering parameters
params.filterByCircularity = True 
params.minCircularity = 0.9
# set Convexity filtering parameters
params.filterByConvexity = False
params.minConvexity = 0.2
# set inertia filtering parameters
params.filterByInertia = True
params.minInertiaRatio = 0.01

# create a detector with the parameters
detector = cv2.SimpleBlobDetector_create(params)
    
# detect blobs
keypoints = detector.detect(image)

# draw blobs on our image as red circles
blank = np.zeros((1,1)) 
blobs = cv2.drawKeypoints(image, keypoints, blank, (0,255,0), cv2.DRAW_MATCHES_FLAGS_DRAW_RICH_KEYPOINTS)

number_of_blobs = len(keypoints)
text = "Number of Circular Blobs: " + str(len(keypoints))
cv2.putText(blobs, text, (20, 550), cv2.FONT_HERSHEY_SIMPLEX, 1, (0, 100, 255), 2)
plt.subplot(2, 2, 2)
plt.title("Filtering Circular Blobs Only")
plt.imshow(blobs)
```

---

#### [**Finding Corners:**](https://www.kaggle.com/code/bulentsiyah/learn-opencv-by-examples-with-python?scriptVersionId=34321869&cellId=32)

* WHY?
* ChatGPT: Corner Harris is a corner detection algorithm.

```python
image = cv2.imread('/path.png')
image = cv2.cvtColor(image, cv2.COLOR_BGR2RGB)
plt.figure(figsize=(10, 10))
gray = cv2.cvtColor(image, cv2.COLOR_BGR2GRAY)

# cornerHarris requires the array datatype to be float32
gray = np.float32(gray)
# 3, size of region for sorbel operator for computing gradients
# 3, size of sobel kernel for derivative computation
# 0.05, from 0.04 to 0.06 were lower is less sensitive and higher is more sensitive for corner detection
harris_corners = cv2.cornerHarris(gray, 3, 3, 0.05)

# dilation of the corner points to enlarge them
kernel = np.ones((7,7),np.uint8)
harris_corners = cv2.dilate(harris_corners, kernel, iterations = 10)

# threshold for an optimal value, it may vary depending on the image.
image[harris_corners > 0.025 * harris_corners.max() ] = [255, 127, 127]

plt.subplot(1, 1, 1)
plt.title("Harris Corners")
plt.imshow(image)
```

---

#### [**Finding match:**]()

* WHY?
* ChatGPT: 

```python
# import where's waldo image
image = cv2.imread('/path.jpg')
image = cv2.cvtColor(image, cv2.COLOR_BGR2RGB)
gray = cv2.cvtColor(image, cv2.COLOR_BGR2GRAY)

plt.figure(figsize=(30, 30))
plt.subplot(2, 2, 1)
plt.title("Where is Waldo?")
plt.imshow(image)

# import grayscale image of waldo
template = cv2.imread('/path.jpg',0)

# find match
result = cv2.matchTemplate(gray, template, cv2.TM_CCOEFF)

# extract corners
min_val, max_val, min_loc, max_loc = cv2.minMaxLoc(result)
top_left = max_loc
bottom_right = (top_left[0] + 50, top_left[1] + 50)

# draw box on image in-place
cv2.rectangle(image, top_left, bottom_right, (0,0,255), 5)

plt.subplot(2, 2, 2)
plt.title("Waldo")
plt.imshow(image)
```

---

#### [**Background Subtraction:**](https://www.kaggle.com/code/bulentsiyah/learn-opencv-by-examples-with-python?scriptVersionId=34321869&cellId=36)

* WHY?
* ChatGPT: Background subtraction (BS) is a common and widely used technique for generating a foreground mask (namely, a binary image containing the pixels belonging to moving objects in the scene) by using static cameras.

```python
algo = 'MOG2'

if algo == 'MOG2':
    # mixture of gaussians
    # better in mixed lighting or complex backgrounds
    # more computationally expensive
    backSub = cv2.createBackgroundSubtractorMOG2()
else:
    # k-nearest neighbors
    # simpler and faster
    # non-parametric
    backSub = cv2.createBackgroundSubtractorKNN()

plt.figure(figsize=(20, 20))
frame = cv2.imread('/path.png')

# apply filter
fgMask = backSub.apply(frame)

plt.subplot(2, 2, 1)
plt.title("Frame")
plt.imshow(cv2.cvtColor(frame, cv2.COLOR_BGR2RGB))

plt.subplot(2, 2, 2)
plt.title("FG Mask")
plt.imshow(cv2.cvtColor(fgMask, cv2.COLOR_BGR2RGB))
                       
frame = cv2.imread('/path.png')

# apply filter
fgMask = backSub.apply(frame)

plt.subplot(2, 2, 3)
plt.title("Frame")
plt.imshow(cv2.cvtColor(frame, cv2.COLOR_BGR2RGB))

plt.subplot(2, 2, 4)
plt.title("FG Mask")
plt.imshow(cv2.cvtColor(fgMask, cv2.COLOR_BGR2RGB))
```

---

#### [**:**]()

* WHY?
* ChatGPT: 

```python
```

---

## **Important Keywords**:

| Keyword | Action |
|-----------------|-----------------|
| |  |
| |  |
| |  |
| |  |
| cv2.rectange() | draw rectangle on image in-place |


---
---
---