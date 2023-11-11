# **Reading Notes: Web Scraping**

---
---
---

## Why are these reading important?

```
Web scraping is a critical automation task that will propell our automation skills beyond our own personal computer.
```

---

## [**Scrape a Dynamic Website with Python:**](https://scrapingant.com/blog/scrape-dynamic-website-with-python)

---

## [**What is Web Scraping?:**](https://en.wikipedia.org/wiki/Web_scraping)

---

## [**How to scrape websites without getting blocked:**](https://www.scrapehero.com/how-to-prevent-getting-blacklisted-while-scraping/)

---

## [**Login and Scrape Data with Playwright and Python:**](https://www.youtube.com/watch?v=H2-5ecFwHHQ&t=60s)

---

## [**Python Playwright Tutorial For Beginners:**](https://www.youtube.com/watch?v=yp1o9biMMWU)

---

## [**Beautiful Soup:**](https://www.crummy.com/software/BeautifulSoup/)

---

## [**Playwright XPath Selectors:**](https://www.programsbuzz.com/article/playwright-xpath-selectors)

---

## [**Xpath Cheatsheet:**](https://devhints.io/xpath)

---

## [**Render Dynamic Pages - Web Scraping Product Links with Python:**](https://www.youtube.com/watch?v=MeBU-4Xs2RU)

---

## [**Rendering Dynamic Pages 2! - Web Scraping ALL products with Python:**](https://www.youtube.com/watch?v=B14mtXA7Tyw)

---

## [**Selecting an element containing certain text:**](https://stackoverflow.com/questions/1520429/is-there-a-css-selector-for-elements-containing-certain-text)

---

## READING QUESTIONS:

1. Prompt: What are the key differences between scraping static and dynamic websites?

  Solution: Static websites are generally much easier to extract accurate information from since all of the information is fixed upon loading/delivery. Where as dynamic websites will deliver the 'shell' that will subsiquently be filled in over time and/or after input is recieved. Working with the timing, provided proper input, and accomodating changes to the html|css|javascript within the page after load contributes to the challenges of webscraping.

1. Prompt: Explain at least three techniques or best practices that can be employed to avoid getting blocked while scraping websites.

  * Follow a websites web scraping quidelines detailed in the 'robots.txt' file.
  * Avoid repetitive, systematic, or fast actions.
  * Route your actions and requests through a IP proxy.
  * Tailor the metadata provided in your requests be more inconspicuous.
  * Use a headless browser to better immulate human web traffic.

1. Prompt: What is Playwright and how does it assist in webscraping tasks? Provide an example of a use case when Playwright would be particularly beneficial.

  Solution: It is an open-source automation tool developed by Microsoft, primarily used for web-scraping. Web scraping examples include data extraction, form submission, automated interactions, navigation, screen capture, authentication, monitor API performance, and so much more.

1. Prompt: Describe the purpose of using Xpath in web scraping, and provide an example of an Xpath expression to select a specific HTML element from a webpage.

  Solution: XML Path Language is used to select elements from a xml document. Follow the steps below to get the Xpath for the image on the google search page.

  * Load the google search page.
  * Right click the image and select 'inspect' from the dropdown.
  * The developer tool will open and highlight the html of the selected element.
  * Right click the html element and hover over 'copy' in the dropdown.
  * Select 'Copy Xpath'.
  
  * //*[@id="hplogo"]

## **What I want to learn more about:**

1. I don't understand the differences between Beautiful Soup, Playwright, Selenium, Pyppeteer, and the Web Scraping API. I need to spend some time familiarizing myself with their respective tasks within web scraping and when one might be benefitial over another.

---
---
---