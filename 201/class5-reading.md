# **Class05 Reading Notes:**
---
---
---

## [**HTML Media:**](https://developer.mozilla.org/en-US/docs/Learn/HTML/Multimedia_and_embedding)

## [**Using Images In HTML:**](https://developer.mozilla.org/en-US/docs/Learn/HTML/Multimedia_and_embedding/Images_in_HTML)

## [**Common Image Types:**](https://developer.mozilla.org/en-US/docs/Web/Media/Formats/Image_types)

## [**Choosing Image Formats:**](https://developer.mozilla.org/en-US/docs/Web/Media/Formats/Image_types#choosing_an_image_format)

* What is a real world use case for the alt attribute being used in a website?

```
If client internet speeds are low or the user has turned off images or Client browser will not display an image. Alt can provide a default message for the browser to display.
```

* How can you improve accessibility of images in an HTML Document?

```
-Provide a good describing with the alt attribute for screen-readers to share with the visually impaired.
-Provide a link in the attributes for the client to follow is the image fails to load.
```

* Provide an example of when the figure element would be useful in an HTML document?

```
When a caption is attached to an image.
```

* Describe the difference between a gif image and an svg image, pretend you are explaining to an elder in your community.

```
If you are looking at a great image on a widscreen tv it is likely to be a vector graphic(svg). These images are stored like blue prints that are built out to fit any scale of screen. Where a gif is a fixed size but can be animated.
```

* What image type would you use to display a screenshot on your website and why?

```
SVG; because I want all users to appreciate my site regardless of what screen they are viewing it from.
```

---

## [**Learn CSS:**](https://developer.mozilla.org/en-US/docs/Learn/CSS)

## [**Using Color in CSS.**](https://developer.mozilla.org/en-US/docs/Web/CSS/CSS_Colors/Applying_color)

## [**Styling HTML Text Elements**](https://developer.mozilla.org/en-US/docs/Learn/CSS/Styling_text/Fundamentals)

* Describe the difference between foreground and background colors of an HTML element, pretend you are talking to someone with no technical knowledge.

```
Background-color: property sets the color of an elements background.
Color: property sets the color of an elements contents(like text).
```

* Your friend asks you to give his colorless blog website a touch up. How would you use color to give his blog some character?

```
I would go find a beautiful color pallete and work with that individual to assign each color in turn to a different element. Perhaps darker colors to his header, footer, and borders; with the lighter colors used as backgrounds for div, section, articles and the body.
```

* What should you consider when choosing fonts from an HTML document?

```
Whether those fonts fit the theme of a page, whether they are readable on most clients devices, or whether they are supported by most client browsers?
```

* What do font-size, font-weight, and font-style do to HTML text elements?

```
font-size: property sets the size of the font
font-weight: property sets the thickness of the font
font-style: property sets the style fo the font (italic, bold...)
```

* Describe two ways you could add spacing around the characters displayed in an h1 element.

```
h1::before, h1::after {
  content:" ";}
//OR
h1 {
  letter-spacing:5px;
}
```

---
---
---
## **Things I want to know more about:**

1. 

