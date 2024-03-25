# **Reading Notes: OpenCV**

---
---
---

## [**OpenCV Examples:**](https://www.kaggle.com/code/bulentsiyah/learn-opencv-by-examples-with-python)

#### [**Image Sharpening:**](https://www.kaggle.com/code/bulentsiyah/learn-opencv-by-examples-with-python?scriptVersionId=34321869&cellId=4)

* WHY?
* ChatGPT: Sharpening is a technique used to enhance the edges and details in an image. It is often employed to improve the visual quality of images and make them appear clearer and more defined. 

```python
# import image
image = cv.imread('/path.jpg')

# convert to usagable version, rgb
image = cv.cvtColor(image, cv.COLOR_BGR2RGB)

# create figure
plt.figure(figsize=(20, 20))

# add current image
plt.subplot(1, 2, 1)
plt.title("Original")
# hide x and y ticks
plt.xticks([]), plt.yticks([])
plt.imshow(image)

# create kernel to apply as filter
# won't normalize since values sum to 1
kernel_sharpening = np.array([[-1,-1,-1], 
                              [-1,9,-1], 
                              [-1,-1,-1]])

# applying different kernels to the input image
sharpened = cv.filter2D(image, -1, kernel_sharpening)

# add new image to figure
plt.subplot(1, 2, 2)
plt.title("Image Sharpening")
plt.imshow(sharpened)

# display figure
plt.show()
```

#### [**Thresholding:**](https://www.kaggle.com/code/bulentsiyah/learn-opencv-by-examples-with-python?scriptVersionId=34321869&cellId=7)

#### [**Another Source:**](https://youtu.be/CdltAssTMs8?feature=shared)

* WHY?
* ChatGPT:  To separate regions of interest in an image from the background or to highlight certain features.

```python
# load image as grayscale
image = cv.imread('/path.jpg', 0)

# create figure
plt.figure(figsize=(30, 30))
# add current image
plt.subplot(3, 2, 1)
plt.title("Original")
plt.imshow(image)

# what, threshold is set by user and fixed
# 127, below goes to 0
# 255, everything above 127 goes to 255
# returns tuple of threshold and new image
ret,thresh1 = cv.threshold(image, 127, 255, cv.THRESH_BINARY)

# add new image to figure
plt.subplot(3, 2, 2)
plt.title("Threshold Binary")
plt.imshow(thresh1)


# what, blur image to reduce noise
# (3,3), larger kernel correlates to more blur
# 0, std of gaussian distribution
image = cv.GaussianBlur(image, (3, 3), 0)

# what, variable threshold applied by pixel's local region
# 255, max value that can be assigned
# ADAPTIVE_THRESH_MEAN_C, method used
# THRESH_BINARY, type of threshold to be applied
# 3, size of local region
# 5, constant subtracted from calculated mean
thresh = cv.adaptiveThreshold(image, 255, cv.ADAPTIVE_THRESH_MEAN_C, cv.THRESH_BINARY, 3, 5) 

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
_, th2 = cv.threshold(image, 0, 255, cv.THRESH_BINARY + cv.THRESH_OTSU)

# add image to figure
plt.subplot(3, 2, 4)
plt.title("Otsu's Thresholding")
plt.imshow(th2)


plt.subplot(3, 2, 5)

# see above
blur = cv.GaussianBlur(image, (5,5), 0)
# see above, to demonstrate effect of blur
_, th3 = cv.threshold(blur, 0, 255, cv.THRESH_BINARY + cv.THRESH_OTSU)

plt.title("Guassian Otsu's Thresholding")
plt.imshow(th3)

# show figure
plt.show()
```

---

#### [**Dilation, Erosion, Opening and Closing:**](https://www.kaggle.com/code/bulentsiyah/learn-opencv-by-examples-with-python?scriptVersionId=34321869&cellId=8)

#### [**Another Source:**](https://youtu.be/xSzsD4kXhRw?feature=shared)

* WHY?
* ChatGPT: Two fundamental morphological operations used to manipulate images based on the shapes contained within them. 

```python
image = cv.imread('/path.jpg')
image = cv.cvtColor(image, cv.COLOR_BGR2RGB)

plt.figure(figsize=(20, 20))
plt.subplot(3, 2, 1)
plt.title("Original")
plt.imshow(image)


# declare kernel, think of them as weights for how surrounding pixels should impact the reassignment of the current pixel
kernel = np.ones((5,5), np.uint8)

# metaphor, think of an island surrounded by a rising sea
# result, fewer lagoons, decreases object size
erosion = cv.erode(image, kernel, iterations = 1)

plt.subplot(3, 2, 2)
plt.title("Erosion")
plt.imshow(erosion)

# metaphor, think of an island in an upwell of the earths crust
# result, more island features, increses object size
dilation = cv.dilate(image, kernel, iterations = 1)
plt.subplot(3, 2, 3)
plt.title("Dilation")
plt.imshow(dilation)


# opening, erosion followed by dilation
# result, smooths boundaries while maintaining size
opening = cv.morphologyEx(image, cv.MORPH_OPEN, kernel)
plt.subplot(3, 2, 4)
plt.title("Opening")
plt.imshow(opening)


# closing, dilation followed by erosion
# result, close small holes or games while maintaining
closing = cv.morphologyEx(image, cv.MORPH_CLOSE, kernel)
plt.subplot(3, 2, 5)
plt.title("Closing")
plt.imshow(closing)
```

---

#### [**Edge Detection and Image Gradients:**](https://www.kaggle.com/code/bulentsiyah/learn-opencv-by-examples-with-python?scriptVersionId=34321869&cellId=10)

#### [**Another Source:**](https://youtu.be/CGfXCkHNemo?feature=shared)

* WHY?
* ChatGPT:  For feature detection, segmentation, and localization.

```python
image = cv.imread('/path.jpg')
image = cv.cvtColor(image, cv.COLOR_BGR2RGB)

# declare height, width, and channels from image
height, width, _ = image.shape

# sorbel, edge detection
# first-order derivative measuring rate of change directly
# less sensitive to noise
# only x and/or y directions
# less computationally expensive

# CV_64F, depth of output image
# 0 and 1, specify direction
# ksize, size of kernel/ local region
# horizontally
sobel_x = cv.Sobel(image, cv.CV_64F, 0, 1, ksize=5)
# vertically
sobel_y = cv.Sobel(image, cv.CV_64F, 1, 0, ksize=5)

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
sobel_OR = cv.bitwise_or(sobel_x, sobel_y)

plt.subplot(3, 2, 4)
plt.title("sobel_OR")
plt.imshow(sobel_OR)

# laplacia, edge detction
# second-order derivative measuring the rate of change
# more sensitive to noise, often paired with noise reduction
# isotropic, detecting edges from all directions
# more computationally expensive

# CV_64F, depth of output image
laplacian = cv.Laplacian(image, cv.CV_64F)

plt.subplot(3, 2, 5)
plt.title("Laplacian")
plt.imshow(laplacian)

# canny, edge detection
# multi-stage algorithm, highly regarded
# noise reduction, image gradients(sorbel), non-maximum suppression, and hysteresis thresholding
# allows for fine-tuning

# 50, lower threshold, below which edges won't be detected
# 120, upper threshold, any pixel above and already a good candidate is more heavily weighted as an edge
canny = cv.Canny(image, 50, 120)

plt.subplot(3, 2, 6)
plt.title("Canny")
plt.imshow(canny)

plt.show()
```

---

#### [**Perpective Shift:**](https://www.kaggle.com/code/bulentsiyah/learn-opencv-by-examples-with-python?scriptVersionId=34321869&cellId=12)

* WHY?
* ChatGPT: Accomodate analysis from different viewpoints or perspectives. 

```python
image = cv.imread('/path.jpg')
image = cv.cvtColor(image, cv.COLOR_BGR2RGB)

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
M = cv.getPerspectiveTransform(points_A, points_B)
 
# what, perspective transformation on image
# M, transformation matrix mapping pixel inputs and outputs
# (420, 594), size of output
# return, new image
warped = cv.warpPerspective(image, M, (420,594))

plt.subplot(1, 2, 2)
plt.title("warpPerspective")
plt.imshow(warped)
```

---

#### [**Scaling, resizing, and interpolations:**]()

* WHY?
* ChatGPT: To further processing.

```python
image = cv.imread('/path.jpg')
image = cv.cvtColor(image, cv.COLOR_BGR2RGB)

plt.figure(figsize=(20, 20))
plt.subplot(2, 2, 1)
plt.title("Original")
plt.imshow(image)

# what, resize image to 75% 
# None, could specify output size instead
image_scaled = cv.resize(image, None, fx=0.75, fy=0.75)

plt.subplot(2, 2, 2)
plt.title("Scaling - Linear Interpolation")
plt.imshow(image_scaled)

# what, resize image to 200%
# INTER_CUBIC, bicubic interpolation method
img_scaled = cv.resize(image, None, fx=2, fy=2, interpolation = cv.INTER_CUBIC)

plt.subplot(2, 2, 3)
plt.title("Scaling - Cubic Interpolation")
plt.imshow(img_scaled)

# (900,400), setting output size instead
# INTER_AREA, often for image downsizing
img_scaled = cv.resize(image, (900, 400), interpolation = cv.INTER_AREA)

plt.subplot(2, 2, 4)
plt.title("Scaling - Skewed Size")
plt.imshow(img_scaled)
```

---

#### [**Pyramid:**](https://www.kaggle.com/code/bulentsiyah/learn-opencv-by-examples-with-python?scriptVersionId=34321869&cellId=16)

#### [**Another Source:**](https://youtu.be/8yvln2atFkA?feature=shared)

* WHY?
* ChatGPT:  Image pyramids are multi-scale representations of an image typically generated by iteratively apply a series of actions to produce a heirarchy of images with progressively reduced resolution.

```python
image = cv.imread('/path.jpg')
image = cv.cvtColor(image, cv.COLOR_BGR2RGB)

plt.figure(figsize=(20, 20))
plt.subplot(2, 2, 1)
plt.title("Original")
plt.imshow(image)

# what, gaussian pyramid construction and manipulation methods

# how, blur then downsampling to create lower resolution version
smaller = cv.pyrDown(image)

# how, upsampling then blur to create a higher resolution version
larger = cv.pyrUp(smaller)

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
image = cv.imread('/path.jpg')
image = cv.cvtColor(image, cv.COLOR_BGR2RGB)

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
image = cv.imread('/kaggle/path.jpg')
image = cv.cvtColor(image, cv.COLOR_BGR2RGB)

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
blurred = cv.filter2D(image, -1, kernel_3x3)

plt.subplot(2, 2, 2)
plt.title("3x3 Kernel Blurring")
plt.imshow(blurred)

# larger kernel
kernel_7x7 = np.ones((7, 7), np.float32) / 49
# more blur
blurred2 = cv.filter2D(image, -1, kernel_7x7)

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
image = cv.imread('/path.png')
image = cv.cvtColor(image, cv.COLOR_BGR2RGB)

plt.figure(figsize=(20, 20))
plt.subplot(2, 2, 1)
plt.title("Original")
plt.imshow(image)

# convet from BGR to grayscale
gray = cv.cvtColor(image,cv.COLOR_BGR2GRAY)

# canny, edge detection
# see above
# returns, binary image
edged = cv.Canny(gray, 30, 200)

plt.subplot(2, 2, 2)
plt.title("Canny Edges")
plt.imshow(edged)

# what, find contours or the points that outline objects
# RETR_EXTERNAL, retrieval mode of contours, external/outer boundary of objects
# CHAIN_APPROX_NONE, stored in output contours list
# return, list of contours/points found and optional output to determine grouping and nesting
contours, hierarchy = cv.findContours(edged, cv.RETR_EXTERNAL, cv.CHAIN_APPROX_NONE)

plt.subplot(2, 2, 3)
plt.title("Canny Edges After Contouring")
plt.imshow(edged)

print("Number of Contours found = " + str(len(contours)))

# what, draws contours on image
# -1, where to draw/store contours
# (0,255,0), color to draw/store them
# 3, pixel width
# in-place
cv.drawContours(image, contours, -1, (0,255,0), 3)

plt.subplot(2, 2, 4)
plt.title("Contours")
plt.imshow(image)
```

---

#### [**Approximate Contours and Convex Hull:**](https://www.kaggle.com/code/bulentsiyah/learn-opencv-by-examples-with-python?scriptVersionId=34321869&cellId=24)

* WHY?
* ChatGPT: Convex hull is a polygon that encloses a set of points. Often representing the outermost contours of an image.

```python
image = cv.imread('/path.jpg')
image = cv.cvtColor(image, cv.COLOR_BGR2RGB)

plt.figure(figsize=(20, 20))
plt.subplot(2, 2, 1)
plt.title("Original")
plt.imshow(image)

# make copy of image
orig_image = image.copy()

# convert to grayscale and segment through threshold
gray = cv.cvtColor(image, cv.COLOR_BGR2GRAY)
ret, thresh = cv.threshold(gray, 127, 255, cv.THRESH_BINARY_INV)

# find contours, see above
contours, hierarchy = cv.findContours(thresh.copy(), cv.RETR_LIST, cv.CHAIN_APPROX_NONE)

# iterate through each contour and compute the bounding rectangle
for c in contours:
    # returns tuple of bounded rect for each object
    x,y,w,h = cv.boundingRect(c)
    # draws rectangle on copy
    cv.rectangle(orig_image,(x,y),(x+w,y+h),(0,0,255),2)

    plt.subplot(2, 2, 2)
    plt.title("Bounding Rectangle")
    plt.imshow(orig_image)

# halt execution until keyboard event, 0=indefinitely
cv.waitKey(0) 
    
# iterate through each contour and compute the approx contour
for c in contours:
    # calculate accuracy as a percent of the contour perimeter(3%)
    accuracy = 0.03 * cv.arcLength(c, True)
    # simplified polygon computed
    # approximate polygon douglas-peucker algorithm
    approx = cv.approxPolyDP(c, accuracy, True)
    # draw to image
    cv.drawContours(image, [approx], 0, (0, 255, 0), 2)
    
    plt.subplot(2, 2, 3)
    plt.title("Approx Poly DP")
    plt.imshow(image)

plt.show()
    
# Convex Hull
image = cv.imread('/path.jpg')
gray = cv.cvtColor(image, cv.COLOR_BGR2GRAY)

plt.figure(figsize=(20, 20))
plt.subplot(1, 2, 1)
plt.title("Original Image")
plt.imshow(image)

ret, thresh = cv.threshold(gray, 176, 255, 0)
contours, hierarchy = cv.findContours(thresh.copy(), cv.RETR_LIST, cv.CHAIN_APPROX_NONE)
    
# sort contours by area and then remove the largest frame contour
n = len(contours) - 1
contours = sorted(contours, key=cv.contourArea, reverse=False)[:n]

# Iterate through contours and draw the convex hull
for c in contours:
    # computes comvex hull
    # encloses the contour while being convex, no internal angles > 180deg
    hull = cv.convexHull(c)
    # drawn onto image, in-place
    cv.drawContours(image, [hull], 0, (0, 255, 0), 2)

    plt.subplot(1, 2, 2)
    plt.title("Convex Hull")
    plt.imshow(image)
```

Between the findContours() and drawContours() functions in OpenCV, there are several useful functions that can be applied to manipulate or process the contours or the image. Some common functions include:

* cv.contourArea(): This function calculates the area of a contour.

* cv.arcLength(): This function calculates the perimeter (arc length) of a contour.

* cv.convexHull(): This function finds the convex hull of a contour.

* cv.boundingRect(): This function calculates the bounding rectangle of a contour.

* cv.minAreaRect(): This function calculates the minimum area rectangle that encloses a contour.

* cv.minEnclosingCircle(): This function calculates the minimum enclosing circle of a contour.

* cv.fitEllipse(): This function fits an ellipse to a contour.

* cv.matchShapes(): This function calculates the similarity between two shapes or contours.

* cv.fillPoly(): This function fills the interior of contours.

---

#### **Draw shapes and write text to images:**

#### [**Another Source:**](https://youtu.be/mVWQNeY1Pb4?feature=shared)

```python
image = cv.imread('/path.jpg')
image = cv.cvtColor(image, cv.COLOR_BGR2RGB)
gray = cv.cvtColor(image, cv.COLOR_BGR2GRAY)

plt.figure(figsize=(20, 20))
plt.subplot(2, 2, 1)
plt.title("Original")
plt.imshow(image)

ret, thresh = cv.threshold(gray, 127, 255, 1)
contours, hierarchy = cv.findContours(thresh.copy(), cv.RETR_LIST, cv.CHAIN_APPROX_NONE)

for cnt in contours:
    # get approximate polygons
    approx = cv.approxPolyDP(cnt, 0.01*cv.arcLength(cnt,True),True)
    # find contour center to place text at the center
    M = cv.moments(cnt)
    cx = int(M['m10'] / M['m00'])
    cy = int(M['m01'] / M['m00'])

    if len(approx) == 3:
        cv.drawContours(image,[cnt],0,(0,255,0),-1)
        cv.putText(image, "Triangle", (cx-50, cy), cv.FONT_HERSHEY_SIMPLEX, 1, (0, 0, 0), 2)
    
    elif len(approx) == 4:
        x,y,w,h = cv.boundingRect(cnt)
        # check to see if 4-side polygon is square or rectangle
        # cv.boundingRect returns the top left and then width and 
        if abs(w-h) <= 3:
            cv.drawContours(image, [cnt], 0, (0, 125 ,255), -1)
            cv.putText(image, "Square", (cx-50, cy), cv.FONT_HERSHEY_SIMPLEX, 1, (0, 0, 0), 2)
        else:
            cv.drawContours(image, [cnt], 0, (0, 0, 255), -1)
            cv.putText(image, "Rectangle", (cx-50, cy), cv.FONT_HERSHEY_SIMPLEX, 1, (0, 0, 0), 2)
            
    elif len(approx) == 10:
        cv.drawContours(image, [cnt], 0, (255, 255, 0), -1)
        cv.putText(image, "Star", (cx-50, cy), cv.FONT_HERSHEY_SIMPLEX, 1, (0, 0, 0), 2)
        
    elif len(approx) >= 15:
        cv.drawContours(image, [cnt], 0, (0, 255, 255), -1)
        cv.putText(image, "Circle", (cx-50, cy), cv.FONT_HERSHEY_SIMPLEX, 1, (0, 0, 0), 2)

plt.subplot(2, 2, 2)
plt.title("Identifying Shapes")
plt.imshow(image)
```

---

#### [**Hough Lines:**](https://www.kaggle.com/code/bulentsiyah/learn-opencv-by-examples-with-python?scriptVersionId=34321869&cellId=28)

#### [**Another Source:**](https://youtu.be/gbL3XKOiBvw?feature=shared)

* WHY?
* ChatGPT: Hough lines is a technique to detect straight lines in an image. Efficient and good with noise

```python
image = cv.imread('/path.png')
image = cv.cvtColor(image, cv.COLOR_BGR2RGB)
gray = cv.cvtColor(image, cv.COLOR_BGR2GRAY)
# see above
edges = cv.Canny(gray, 100, 170, apertureSize = 3)

plt.figure(figsize=(20, 20))
plt.subplot(2, 2, 1)
plt.title("edges")
plt.imshow(edges)

# calculate HoughLines using a rho accuracy of 1 pixel
# theta accuracy of np.pi / 180 which is 1 degree
# threshold is set to 200points to make a line
lines = cv.HoughLines(edges, 1, np.pi/180, 200)

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
    cv.line(image, (x1, y1), (x2, y2), (255, 0, 0), 2)

# lines = cv.HoghLinesP(edges, 1, np.pi/180, 100, minLineLength=100, maxLineGap=10)

# for line in lines:
#   x1,y1,x2,y2 = line[0]
#   cv.line(img,(x1,y1), (x2, y2),(255,0,0),2)

plt.subplot(2, 2, 2)
plt.title("Hough Lines")
plt.imshow(image)
```

---

#### [**Counting Circles and Ellipses:**](https://www.kaggle.com/code/bulentsiyah/learn-opencv-by-examples-with-python?scriptVersionId=34321869&cellId=30)

#### [**Another Source:**](https://youtu.be/dp1r9oT_h9k?feature=shared)

```python
image = cv.imread('/path.jpg')
image = cv.cvtColor(image, cv.COLOR_BGR2RGB)
plt.figure(figsize=(20, 20))

# intialize the detector using the default parameters
detector = cv.SimpleBlobDetector_create()
# detect blobs
keypoints = detector.detect(image)
 
# draw blobs on image as red circles
blank = np.zeros((1,1)) 
blobs = cv.drawKeypoints(image, keypoints, blank, (0,0,255), cv.DRAW_MATCHES_FLAGS_DRAW_RICH_KEYPOINTS)

number_of_blobs = len(keypoints)
text = "Total Number of Blobs: " + str(len(keypoints))
cv.putText(blobs, text, (20, 550), cv.FONT_HERSHEY_SIMPLEX, 1, (100, 0, 255), 2)
plt.subplot(2, 2, 1)
plt.title("Blobs using default parameters")
plt.imshow(blobs)

# initialize parameter setting using cv.SimpleBlobDetector
params = cv.SimpleBlobDetector_Params()
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
detector = cv.SimpleBlobDetector_create(params)
    
# detect blobs
keypoints = detector.detect(image)

# draw blobs on our image as red circles
blank = np.zeros((1,1)) 
blobs = cv.drawKeypoints(image, keypoints, blank, (0,255,0), cv.DRAW_MATCHES_FLAGS_DRAW_RICH_KEYPOINTS)

number_of_blobs = len(keypoints)
text = "Number of Circular Blobs: " + str(len(keypoints))
cv.putText(blobs, text, (20, 550), cv.FONT_HERSHEY_SIMPLEX, 1, (0, 100, 255), 2)
plt.subplot(2, 2, 2)
plt.title("Filtering Circular Blobs Only")
plt.imshow(blobs)
```

```python
img = cv.imread('smarties.png')
output = img.copy()
gray = cv.cvtColor(img, cv.COLOR_BGR2GRAY)
gray = cv.medianBlur(gray, 5)
circles = cv.HoughCircles(gray, cv.HOUGH_GRADIENT, 1, 20,
                          param1=50, param2=30, minRadius=0, maxRadius=0)
detected_circles = np.uint16(np.around(circles))
for (x, y ,r) in detected_circles[0, :]:
    # circle
    cv.circle(output, (x, y), r, (0, 0, 0), 3)
    # center
    cv.circle(output, (x, y), 2, (0, 255, 255), 3)


cv.imshow('output',output)
cv.waitKey(0)
cv.destroyAllWindows()
```

---

#### [**Finding Corners:**](https://www.kaggle.com/code/bulentsiyah/learn-opencv-by-examples-with-python?scriptVersionId=34321869&cellId=32)

#### [**Another Source:**](https://youtu.be/XJXWOqvj1So?feature=shared)

* WHY?
* ChatGPT: Corner Harris is a corner detection algorithm.

```python
image = cv.imread('/path.png')
image = cv.cvtColor(image, cv.COLOR_BGR2RGB)
plt.figure(figsize=(10, 10))
gray = cv.cvtColor(image, cv.COLOR_BGR2GRAY)

# cornerHarris requires the array datatype to be float32
gray = np.float32(gray)
# 3, size of region for sorbel operator for computing gradients
# 3, size of sobel kernel for derivative computation
# 0.05, from 0.04 to 0.06 were lower is less sensitive and higher is more sensitive for corner detection
harris_corners = cv.cornerHarris(gray, 3, 3, 0.05)

# dilation of the corner points to enlarge them
kernel = np.ones((7,7),np.uint8)
harris_corners = cv.dilate(harris_corners, kernel, iterations = 10)

# threshold for an optimal value, it may vary depending on the image.
image[harris_corners > 0.025 * harris_corners.max() ] = [255, 127, 127]

plt.subplot(1, 1, 1)
plt.title("Harris Corners")
plt.imshow(image)
```

```python
img = cv.imread('path.png')
gray = cv.cvtColor(img, cv.COLOR_BGR2GRAY)

# 100, max number of corners to detect
# 0.01, quality level
# 10, minimum distance between corners
corners = cv.goodFeaturesToTrack(gray, 100, 0.01, 10)

# convert into integers
corners = np.int0(corners)

for i in corners:
    # unravel multi-dim array into one-dim array
    # x, y, i[0], i[1]
    x, y = i.ravel()
    cv.circle(img, (x, y), 3, [255, 255, 0], -1)

cv.imshow('Shi-Tomasi Corner Detector', img)

if cv.waitKey(0) & 0xff == 27:
    cv.destroyAllWindows()
```

---

#### [**Template Matching:**](https://www.kaggle.com/code/bulentsiyah/learn-opencv-by-examples-with-python?scriptVersionId=34321869&cellId=34)

#### [**Another Source:**](https://youtu.be/sghglbXyjHc?feature=shared)

```python
# import where's waldo image
image = cv.imread('/path.jpg')
image = cv.cvtColor(image, cv.COLOR_BGR2RGB)
gray = cv.cvtColor(image, cv.COLOR_BGR2GRAY)

plt.figure(figsize=(30, 30))
plt.subplot(2, 2, 1)
plt.title("Where is Waldo?")
plt.imshow(image)

# import grayscale image of waldo
template = cv.imread('/path.jpg',0)

# find match
result = cv.matchTemplate(gray, template, cv.TM_CCOEFF)

# extract corners
min_val, max_val, min_loc, max_loc = cv.minMaxLoc(result)
top_left = max_loc
bottom_right = (top_left[0] + 50, top_left[1] + 50)

# draw box on image in-place
cv.rectangle(image, top_left, bottom_right, (0,0,255), 5)

plt.subplot(2, 2, 2)
plt.title("Waldo")
plt.imshow(image)
```

---

#### [**Background Subtraction:**](https://www.kaggle.com/code/bulentsiyah/learn-opencv-by-examples-with-python?scriptVersionId=34321869&cellId=36)

#### [**Another Source:**](https://youtu.be/eZ2kDurOodI?feature=shared)

* WHY?
* ChatGPT: Background subtraction (BS) is a common and widely used technique for generating a foreground mask (namely, a binary image containing the pixels belonging to moving objects in the scene) by using static cameras.

```python
algo = 'MOG2'

if algo == 'MOG2':
    # mixture of gaussians
    # better in mixed lighting or complex backgrounds
    # more computationally expensive
    backSub = cv.createBackgroundSubtractorMOG2()
else:
    # k-nearest neighbors
    # simpler and faster
    # non-parametric
    backSub = cv.createBackgroundSubtractorKNN()

plt.figure(figsize=(20, 20))
frame = cv.imread('/path.png')

# apply filter
fgMask = backSub.apply(frame)

plt.subplot(2, 2, 1)
plt.title("Frame")
plt.imshow(cv.cvtColor(frame, cv.COLOR_BGR2RGB))

plt.subplot(2, 2, 2)
plt.title("FG Mask")
plt.imshow(cv.cvtColor(fgMask, cv.COLOR_BGR2RGB))
                       
frame = cv.imread('/path.png')

# apply filter
fgMask = backSub.apply(frame)

plt.subplot(2, 2, 3)
plt.title("Frame")
plt.imshow(cv.cvtColor(frame, cv.COLOR_BGR2RGB))

plt.subplot(2, 2, 4)
plt.title("FG Mask")
plt.imshow(cv.cvtColor(fgMask, cv.COLOR_BGR2RGB))
```

```python
image = cv2.imread('road.jpg')
image = cv2.cvtColor(image, cv2.COLOR_BGR2RGB)

print(image.shape)
height = image.shape[0]
width = image.shape[1]

region_of_interest_vertices = [
    (0, height),
    (width/2, height/2),
    (width, height)
]

def region_of_interest(img, vertices):
    mask = np.zeros_like(img)
    channel_count = img.shape[2]
    match_mask_color = (255,) * channel_count
    # create white area of interest
    cv2.fillPoly(mask, vertices, match_mask_color)
    # mask over areas
    masked_image = cv2.bitwise_and(img, mask)
    return masked_image

cropped_image = region_of_interest(image,
                np.array([region_of_interest_vertices], np.int32),)
```

## [**freeCodeCamp Video**:](https://youtu.be/oXlwWbU8l2o?feature=shared)

---

#### [**Load Images or Videos:**](https://youtu.be/oXlwWbU8l2o?feature=shared&t=254)

#### [**Another Source:**](https://youtu.be/-RtVZsCvXAQ?feature=shared)

```python
# read image
img = cv.imread('./path.jpg')
# show window with image
cv.imshow('Cats', img)
# pause execution until keystroke
cv.waitKey(0)

# Reading Videos
capture = cv.VideoCapture('./path.mp4')
fourcc = cv.VideoWriter_fourcc(*'XVID')
output = cv.VideoWriter('output.avi',fourcc, 20.0, (640,480))

old_width = int(capture.get(cv.CAP_PROP_FRAME_WIDTH))
old_height = int(capture.get(cv.CAP_PROP_FRAME_HEIGHT))

new_height = 480  
new_width = int((new_height / old_height)*old_width)

# loop through video
while True:
    isTrue, frame = capture.read()
    
    # if cv.waitKey(20) & 0xFF==ord('d'):
    # This is the preferred way - if `isTrue` is false (the frame could 
    # not be read, or we're at the end of the video), we immediately
    # break from the loop. 
    if isTrue:    
        # resize
        frame_resized = cv.resize(frame, (new_width, new_height))
        # save to output video
        output.write(frame_resized)
        # show
        cv.imshow('Video', frame_resized)
        # cancel at d keystroke
        if cv.waitKey(20) & 0xFF==ord('d'):
            break            
    else:
        break

capture.release()
output.release()
cv.destroyAllWindows()
```

---

#### [**Draw Shapes and Add text:**](https://youtu.be/oXlwWbU8l2o?feature=shared&t=1222)

#### [**Another Source:**](https://youtu.be/V1aMDD5583k?feature=shared)

```python
blank = np.zeros((500,500,3), dtype='uint8')

# 1. Paint the image a certain colour
blank[200:300, 300:400] = 0,255,0

# 2. Draw a Rectangle
cv.rectangle(blank, (0,0), (blank.shape[1]//2, blank.shape[0]//2), (0,255,0), thickness=-1)

# 3. Draw A circle
cv.circle(blank, (blank.shape[1]//2, blank.shape[0]//2), 40, (0,0,255), thickness=-1)

# 4. Draw a line
cv.line(blank, (100,250), (300,400), (255,255,255), thickness=3)

# 5. Write text
cv.putText(blank, 'Hello, my name is Jacob!!!', (0,225), cv.FONT_HERSHEY_TRIPLEX, 1.0, (0,255,0), 2)
```

---

#### [**Basic Functions:**](https://youtu.be/oXlwWbU8l2o?feature=shared&t=1916)

```python
img = cv.imread("./path.jpg")

# Translation
def translate(img, x, y):
    # transformation matrix specifying the translation, scaling, rotation, and/or shear operations to be applied to the image.
    transMat = np.float32([[1, 0, x], [0, 1, y]])
    dimensions = (img.shape[1], img.shape[0])
    # affine transformation preserve points, straight lines and planes
    return cv.warpAffine(img, transMat, dimensions)

translated = translate(img, -100, 100)

# Rotation
def rotate(img, angle, rotPoint=None):
    (height, width) = img.shape[:2]

    if rotPoint is None:
        rotPoint = (width // 2, height // 2)

    # generate matrix
    # rotPoint, rotation origin
    # angle, how far to rotate
    # 1.0, keep scale the same
    rotMat = cv.getRotationMatrix2D(rotPoint, angle, 1.0)
    dimensions = (width, height)
    # affine transformation preserve points, straight lines and planes  
    return cv.warpAffine(img, rotMat, dimensions)

rotated = rotate(img, -45)

rotated_rotated = rotate(img, -90)

# Resizing
resized = cv.resize(img, (500, 500), interpolation=cv.INTER_CUBIC)

# Flipping
# 0: x-axis, 1: y-axis, -1: both
flip = cv.flip(img, -1)

# Cropping
cropped = img[200:400, 300:400]
```

---

#### [**Contours:**](https://youtu.be/oXlwWbU8l2o?feature=shared&t=3430)

#### [**Another Source:**](https://youtu.be/FbR9Xr0TVdY?feature=shared)

```python
img = cv.imread('./path.jpg')

blank = np.zeros(img.shape, dtype='uint8')

gray = cv.cvtColor(img, cv.COLOR_BGR2GRAY)

# blur to reduce noise
blur = cv.GaussianBlur(gray, (5,5), cv.BORDER_DEFAULT)

# generate image with detected edges
canny = cv.Canny(blur, 125, 175)

# generate list of contours/points from image of edges
contours, hierarchies = cv.findContours(canny, cv.RETR_LIST, cv.CHAIN_APPROX_SIMPLE)

# draw countour points onto blank image
cv.drawContours(blank, contours, -1, (0,0,255), 1)
```

---

#### [**Convert between colors:**](https://youtu.be/oXlwWbU8l2o?feature=shared&t=4373)

```python
img = cv.imread('./path.jpg')

# BGR to Grayscale
gray = cv.cvtColor(img, cv.COLOR_BGR2GRAY)

# BGR to HSV
hsv = cv.cvtColor(img, cv.COLOR_BGR2HSV)

# BGR to L*a*b
lab = cv.cvtColor(img, cv.COLOR_BGR2LAB)

# BGR to RGB
rgb = cv.cvtColor(img, cv.COLOR_BGR2RGB)

# HSV to BGR
lab_bgr = cv.cvtColor(lab, cv.COLOR_LAB2BGR)
```

---

#### [**Image Split and Merge:**](https://youtu.be/oXlwWbU8l2o?feature=shared&t=4994)

* WHY?
* ChatGPT: Separating out the different channels from one image. 

```python
img = cv.imread('./path.jpg')

blank = np.zeros(img.shape[:2], dtype='uint8')

b,g,r = cv.split(img)

cv.imshow('Blue', b) # grayscale of only blue channel
cv.imshow('Green', g) # grayscale of only green channel
cv.imshow('Red', r) # grayscale of only red channel

blue = cv.merge([b,blank,blank])
green = cv.merge([blank,g,blank])
red = cv.merge([blank,blank,r])

cv.imshow('Blue', blue) # only blue channel
cv.imshow('Green', green) # only green channel
cv.imshow('Red', red) # only red channel

print(img.shape) # (427, 640, 3)
print(b.shape) # (427, 640)
print(g.shape) # (427, 640)
print(r.shape) # (427, 640)

merged = cv.merge([b,g,r])
cv.imshow('Merged Image', merged)
```

---

#### [**Blur, Smoothing, and Averaging:**](https://youtu.be/oXlwWbU8l2o?feature=shared&t=5473)

#### [**Another Source:**](https://youtu.be/u3poUhCxx4k?feature=shared)

```python
img = cv.imread('./path.jpg')

# Averaging
# applys average from kernel
average = cv.blur(img, (3,3))

# Gaussian Blur
gauss = cv.GaussianBlur(img, (3,3), 0)

# Median Blur
# applys median from kernel
median = cv.medianBlur(img, 3)

# Bilateral, most common bluring
# good at retaining edges while blurring
# 10, size of kernel
# 35, sigmaColor controls similarity between neighbors, smaller less smoothing
# 25, sigmaSpace controls range of comparison
bilateral = cv.bilateralFilter(img, 10, 35, 25)
```

---

#### [**Bitwise Operators:**](https://youtu.be/oXlwWbU8l2o?feature=shared&t=6284)

* WHY?
* ChatGPT: Very important for generating masks.

```python
blank = np.zeros((400,400), dtype='uint8')

rectangle = cv.rectangle(blank.copy(), (30,30), (370,370), 255, -1)
circle = cv.circle(blank.copy(), (200,200), 200, 255, -1)

cv.imshow('Rectangle', rectangle) # white rectangle with black background
cv.imshow('Circle', circle) # white circle with black background

bitwise_and = cv.bitwise_and(rectangle, circle)
cv.imshow('Bitwise AND', bitwise_and) # white intersection of rectangle and circle

bitwise_or = cv.bitwise_or(rectangle, circle)
cv.imshow('Bitwise OR', bitwise_or) # white union of rectangle and circle

bitwise_xor = cv.bitwise_xor(rectangle, circle)
cv.imshow('Bitwise XOR', bitwise_xor) # white non-overlapping xor of rectangle and circle

# bitwise NOT
bitwise_not = cv.bitwise_not(circle)
cv.imshow('Circle NOT', bitwise_not) # white background and black circle
```

---

#### [**Masking:**](https://youtu.be/oXlwWbU8l2o?feature=shared&t=6786)

#### [**Another Source:**](https://youtu.be/mc846qb0ngk?feature=shared)

* WHY?
* ChatGPT: Selectively applying or removing certain parts of the image based on a binary mask. A mask is a binary image where pixels are either set to 0 (black) or 1 (white), indicating areas of interest or regions to be ignored.

```python
img = cv.imread('./path.jpg')

blank = np.zeros(img.shape[:2], dtype='uint8')

circle = cv.circle(blank.copy(), (img.shape[1]//2 + 45,img.shape[0]//2), 100, 255, -1)

rectangle = cv.rectangle(blank.copy(), (30,30), (370,370), 255, -1)

weird_shape = cv.bitwise_and(circle,rectangle)

masked = cv.bitwise_and(img,img,mask=weird_shape)
```

---

#### [**Color Channel Histogram:**](https://youtu.be/oXlwWbU8l2o?feature=shared&t=7307)

#### [**Another Source:**](https://youtu.be/F9TZb0XBow0?feature=shared)

* WHY?
* ChatGPT: A color histogram for an image involves quantifying the distribution of colors present in the image across different color channels.The color histogram provides valuable insights into the color composition and distribution of the image.

```python
img = cv.imread('./path.jpg')

blank = np.zeros(img.shape[:2], dtype='uint8')

mask = cv.circle(blank, (img.shape[1]//2,img.shape[0]//2), 100, 255, -1)

plt.figure()
plt.title('Colour Histogram')
plt.xlabel('Bins')
plt.ylabel('# of pixels')
colors = ('b', 'g', 'r')

for i,col in enumerate(colors):
    # [img], accepts list of images
    # [i], specified channels
    # mask, use mask or None
    # [256], number of bins
    # [0,256], range for bins
    hist = cv.calcHist([img], [i], mask, [256], [0,256])
    plt.plot(hist, color=col)
    plt.xlim([0,256])

plt.show()
```

---

#### [**Thresholding:**](https://youtu.be/oXlwWbU8l2o?feature=shared&t=8122)

* WHY?
* ChatGPT: Segment images by dividing them into regions based on pixel intensity values. The process involves comparing each pixel value in an image to a threshold value and classifying the pixels as either foreground or background based on whether their intensity values are above or below the threshold.

```python
img = cv.imread('./path.jpg')

gray = cv.cvtColor(img, cv.COLOR_BGR2GRAY)

# 150, threshold intensity
# 255, max intensity to reassign pixels
# THRESH_BINARY, binary assignment method
# THRESH_TRUNC, greater truncated down
# THRESH_TOZERO, lesser reduced to zero
threshold, thresh = cv.threshold(gray, 150, 255, cv.THRESH_BINARY )

# THRESH_BINARY_INV, greater are set to 0, less than or equal unchanged
threshold, thresh_inv = cv.threshold(gray, 150, 255, cv.THRESH_BINARY_INV )

# ADAPTIVE_THRESH_GAUSSIAN_C, threshold is weighted sum of local minus constant
# ADAPTIVE_THRESH_MEAN_C, threshold is mean of local minus constant
# 11, block size of local 
# 9, constant
adaptive_thresh = cv.adaptiveThreshold(gray, 255, cv.ADAPTIVE_THRESH_GAUSSIAN_C, cv.THRESH_BINARY_INV, 11, 9)
```

---

#### [**Edge Detection:**](https://youtu.be/oXlwWbU8l2o?feature=shared&t=8788)

#### [**Another Source:**](https://youtu.be/aDY4aBLFOIg?feature=shared)

```python
img = cv.imread('./path.jpg')
gray = cv.cvtColor(img, cv.COLOR_BGR2GRAY)

# Laplacian, compute gradients of image
lap = cv.Laplacian(gray, cv.CV_64F)
# convert to abs to visualize
lap = np.uint8(np.absolute(lap))

# Sobel, x axis gradients
sobelx = cv.Sobel(gray, cv.CV_64F, 1, 0)
# y axis gradients
sobely = cv.Sobel(gray, cv.CV_64F, 0, 1)
# combine x and y
combined_sobel = cv.bitwise_or(sobelx, sobely)

# find gradients/edge with Canny Algorithm
canny = cv.Canny(gray, 150, 175)
```

---

#### [**Face Detection:**](https://youtu.be/oXlwWbU8l2o?feature=shared&t=9327)

#### [**Another Source:**](https://youtu.be/LopYA64KmdE?feature=shared)

* What is the difference between Haar Cascades and Local Binary Patterns?
* ChatGPT: Both feature extraction techniques commonly used in object detection and recognition tasks.
  * Haar cascades use a cascaded series of classifiers to detect objects based on the presence of specific Haar-like features at different scales and positions in an image. These classifiers are trained using machine learning techniques, such as the AdaBoost algorithm. Common for object detection, effective for distinct texture and shapes.
  * LBP features are extracted by computing histograms of local binary patterns over regions of an image. These histograms capture the distribution of texture patterns in different regions of the image. Common for texture classification and objects with patterns.

```python
img = cv.imread('./path.jpg')

gray = cv.cvtColor(img, cv.COLOR_BGR2GRAY)

# create a haar cascade classifier instance
# https://github.com/opencv/opencv/tree/4.x/data/haarcascades
haar_cascade = cv.CascadeClassifier('./path/haar_face.xml')

# detect multiple faces
faces_rect = haar_cascade.detectMultiScale(gray, scaleFactor=1.1, minNeighbors=1)

print(f'Number of faces found = {len(faces_rect)}')

for (x,y,w,h) in faces_rect:
    cv.rectangle(img, (x,y), (x+w,y+h), (0,255,0), thickness=2)

cv.imshow('Detected Faces', img)
```

---

#### [**Face Recognition:**](https://youtu.be/oXlwWbU8l2o?feature=shared&t=10151)

##### Training

```python
people = ['Ben Afflek', 'Elton John', 'Jerry Seinfield', 'Madonna', 'Mindy Kaling']
DIR = r'/Users/jacobbassett/projects/courses/opencv/opencv-course/Resources/Faces/train'

haar_cascade = cv.CascadeClassifier('./faces/haar_face.xml')

features = []
labels = []

def create_train():
    for idx, person in enumerate(people):
        path = os.path.join(DIR, person)

        for img in os.listdir(path):
            img_path = os.path.join(path,img)

            img_array = cv.imread(img_path)
            if img_array is None:
                continue 
                
            gray = cv.cvtColor(img_array, cv.COLOR_BGR2GRAY)

            faces_rect = haar_cascade.detectMultiScale(gray, scaleFactor=1.1, minNeighbors=4)

            for (x,y,w,h) in faces_rect:
                faces_roi = gray[y:y+h, x:x+w]
                features.append(faces_roi)
                labels.append(idx)

create_train()
print('Training done ---------------')

features = np.array(features, dtype='object')
labels = np.array(labels)

face_recognizer = cv.face.LBPHFaceRecognizer_create()

# Train the Recognizer on the features list and the labels list
face_recognizer.train(features,labels)

face_recognizer.save('./faces/face_trained.yml')
np.save('./faces/features.npy', features)
np.save('./faces/labels.npy', labels)
```

##### Facial Recognition

```python
haar_cascade = cv.CascadeClassifier('./faces/haar_face.xml')

people = ['Ben Afflek', 'Elton John', 'Jerry Seinfield', 'Madonna', 'Mindy Kaling']

face_recognizer = cv.face.LBPHFaceRecognizer_create()
face_recognizer.read('./faces/face_trained.yml')

img = cv.imread(r'./Resources/Faces/val/elton_john/1.jpg')

gray = cv.cvtColor(img, cv.COLOR_BGR2GRAY)

# Detect the face in the image
faces_rect = haar_cascade.detectMultiScale(gray, 1.1, 4)

for (x,y,w,h) in faces_rect:
    faces_roi = gray[y:y+h,x:x+w]

    label, confidence = face_recognizer.predict(faces_roi)<>

    cv.putText(img, str(people[label]), (20,20), cv.FONT_HERSHEY_COMPLEX, 1.0, (0,255,0), thickness=2)
    cv.rectangle(img, (x,y), (x+w,y+h), (0,255,0), thickness=2)

cv.imshow('Detected Face', img)
```

---

#### [**Mouse Events:**](https://youtu.be/rrh-4NtuK-w?feature=shared)

#### [**Another Source:**](https://youtu.be/a7_dBO3EAng?feature=shared)

* WHY?
* ChatGPT: You can extract image data based on mouse events.

```python
def click_event(event, x, y, flags, param):
    font = cv.FONT_HERSHEY_SIMPLEX
    # displays coordinates on left click
    if event == cv.EVENT_LBUTTONDOWN:
        strXY = str(x) + ', '+ str(y)
        cv.putText(img, strXY, (x, y), font, .5, (255, 255, 0), 2)
        cv.imshow('image', img)
    # displays rgb on right click
    if event == cv.EVENT_RBUTTONDOWN:
        blue, green, red, = img[y, x, 0], img[y, x, 1], img[y, x, 2]
        strBGR = str(blue) + ', '+ str(green)+ ', '+ str(red)
        cv.putText(img, strBGR, (x, y), font, .5, (0, 255, 255), 2)
        cv.imshow('image', img)

img = cv.imread('path.jpg')
cv.imshow('image', img)

cv.setMouseCallback('image', click_event)

cv.waitKey(0)
cv.destroyAllWindows()
```

---

#### [**Track Bar:**](https://youtu.be/3D7O_kZi8-o?feature=shared)

* WHAT: Open a tracking window to change the mask and filter the image.

```python
def nothing(x):
    pass

cv.namedWindow("Tracking")
cv.createTrackbar("LH", "Tracking", 0, 255, nothing)
cv.createTrackbar("LS", "Tracking", 0, 255, nothing)
cv.createTrackbar("LV", "Tracking", 0, 255, nothing)
cv.createTrackbar("UH", "Tracking", 255, 255, nothing)
cv.createTrackbar("US", "Tracking", 255, 255, nothing)
cv.createTrackbar("UV", "Tracking", 255, 255, nothing)

while True:
    frame = cv.imread('path.png')

    hsv = cv.cvtColor(frame, cv.COLOR_BGR2HSV)

    l_h = cv.getTrackbarPos("LH", "Tracking")
    l_s = cv.getTrackbarPos("LS", "Tracking")
    l_v = cv.getTrackbarPos("LV", "Tracking")

    u_h = cv.getTrackbarPos("UH", "Tracking")
    u_s = cv.getTrackbarPos("US", "Tracking")
    u_v = cv.getTrackbarPos("UV", "Tracking")

    l_b = np.array([l_h, l_s, l_v])
    u_b = np.array([u_h, u_s, u_v])

    mask = cv.inRange(hsv, l_b, u_b)

    res = cv.bitwise_and(frame, frame, mask=mask)

    cv.imshow("frame", frame)
    cv.imshow("mask", mask)
    cv.imshow("res", res)

    key = cv.waitKey(1)
    if key == 27:
        break

cv.destroyAllWindows()
```

---

#### [**Video Tracking:**](https://youtu.be/MkcUgPhOlP8?feature=shared)

```python
cap = cv.VideoCapture('path.avi')

frame_width = int( cap.get(cv.CAP_PROP_FRAME_WIDTH))
frame_height =int( cap.get( cv.CAP_PROP_FRAME_HEIGHT))

fourcc = cv.VideoWriter_fourcc('X','V','I','D')
out = cv.VideoWriter("output.avi", fourcc, 5.0, (1280,720))

ret, frame1 = cap.read()
ret, frame2 = cap.read()

while cap.isOpened():
    # make grayscale of difference
    diff = cv.absdiff(frame1, frame2)
    gray = cv.cvtColor(diff, cv.COLOR_BGR2GRAY)
    # blur
    blur = cv.GaussianBlur(gray, (5,5), 0)
    # threshold
    _, thresh = cv.threshold(blur, 20, 255, cv.THRESH_BINARY)
    # dilate
    dilated = cv.dilate(thresh, None, iterations=3)
    # contours
    contours, _ = cv.findContours(dilated, cv.RETR_TREE, cv.CHAIN_APPROX_SIMPLE)

    for contour in contours:
        (x, y, w, h) = cv.boundingRect(contour)
        # filter out small objects that move
        if cv.contourArea(contour) < 900: continue
        # draw rect and text
        cv.rectangle(frame1, (x, y), (x+w, y+h), (0, 255, 0), 2)
        cv.putText(frame1, "Status: {}".format('Movement'), (10, 20), cv.FONT_HERSHEY_SIMPLEX, 1, (0, 0, 255), 3)

    image = cv.resize(frame1, (1280,720))
    out.write(image)
    cv.imshow("feed", frame1)
    frame1 = frame2
    ret, frame2 = cap.read()

    if cv.waitKey(40) == 27:
        break

cv.destroyAllWindows()
cap.release()
out.release()
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
---
---