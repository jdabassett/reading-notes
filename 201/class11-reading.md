# **Class11 Reading Notes:**
---
---
---

## [**Video and Audio Content:**](https://developer.mozilla.org/en-US/docs/Learn/HTML/Multimedia_and_embedding/Video_and_audio_content)

* Explain how the ability to use video and audio on the web has evolved since the early 2000s.

```
Both used to be supported through extensions like Flash and Silverlight; but these were to much of a security risk and had accessibilty issues.
```

* Describe the use of the src and controls attributes in the video element.

```
The src attribute provide a link to the source of a video and audio element.
The control attribute is a binary over whether the client is provided with controls with a given video and audio element.
```

* Why is it important to have fallback content inside the video element?

```
Provide an alternative if the video doesn't load.
```

* Write a very short story where audio and video are characters.

```
Once upon a time someone wanted to add audio and video elements to their webpage but didn't want to summon Flash or Silverlight from the underworld. So that developer knelt down and prayered to the god's Video and Audio. Whom collect make it in time to answer their prayer so they used a P and A as a fallback.
```

---

## [**A Complete Guide to Grid:**](https://css-tricks.com/snippets/css/complete-guide-grid/)

* How does Grid layout differ from Flex?

```
Flex is primary for aligning element on one line.
Gride is for aligning elements on multiple parallel lines.
```

* Grid container, grid item, and grid lines are a few important terms to understand when using Grid. Please describe these terms in a few sentences.

```
Grid Container: is the parent element.
Grid Item: are the children elements.
Grid Lines: are the vertical and horizontal lines that set the borders between rows and columns.
```

---

## [**Responsive Images:**](https://developer.mozilla.org/en-US/docs/Learn/HTML/Multimedia_and_embedding/Responsive_images)

* Besides making a site visually appealing across different screen sizes, why should developers make images responsive?

```
So that they can function as intended over a wide array of devices and internet connection speeds.
```

* Define the following img attributes srcset and sizes. Write an example of how they are used.

```
srcset: Points to a separate source for an image to be used when the hints specificed with 'sizes' are meet.

Example:
<img
  srcset="two.jpg 480w, three.jpg 800w"
  sizes="(max-width: 600px) 480px, 800px"
  src="one.jpg"
  alt="description" />
The above provide two separate images for different device widths.
```

* How is srcset more helpful for responsive images than CSS or JavaScript?

```
A webpage loads images before any CSS or JavaScript is loaded or parsed. So srcset can load the best image while loading.
```

---

## [**Images in HTML:**](https://developer.mozilla.org/en-US/docs/Learn/HTML/Multimedia_and_embedding/Images_in_HTML)

## [**Other Embedding Technologies:**](https://developer.mozilla.org/en-US/docs/Learn/HTML/Multimedia_and_embedding/Other_embedding_technologies)


---
---
---
## **Things I want to know more about:**

1. What the most common security problems are with webpages and how to guard against them.

