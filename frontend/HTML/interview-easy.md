
# Interview - Easy

### Questions
1. [What is the difference between HTML and HTML5?](#1-what-is-the-difference-between-html-and-html5)
2. [How do you create a hyperlink in HTML?](#2-how-do-you-create-a-hyperlink-in-html)
3. [What is the purpose of the `<alt>` attribute in the `<img>` tag?](#3-what-is-the-purpose-of-the-alt-attribute-in-the-img-tag)
4. [How do you include a comment in HTML?](#4-how-do-you-include-a-comment-in-html)
5. [What are Non-Semantic & Semantic tags in HTML?](#5-what-are-non-semantic--semantic-tags-in-html)
6. [How do you create an ordered and unordered list in HTML?](#)
7. [How can you display an image in HTML?](#)
8. [How do you create a form with text input and a submit button?](#)
9. [How do you make text bold or italic in HTML?](#)
10. [How do you create a hyperlink that opens in a new tab?](#)

---

### Answers

#### 1. What is the difference between HTML and HTML5?
## HTML ##
 - Combination of Hypertext and Markup language
 - **Hypertext** - defines the link between the web pages
 - **Markup Language** - used to define the text document within the tag which defines the structure of web pages
 - Used to annotate text so that a machine can understand it and manipulate text accordingly

 ## HTML5 ##
 - Introduced application programming interfaces(`API`) and Document Object Model(`DOM`)
 - Introduced new semantic elements like `<header>`, `<footer>`, `<section>`, and `<article>` for improved structure
 - Enhances multimedia capabilities with native support for audio and video elements
 - Provides the localStorage API, allowing web applications to store data locally on the user’s device
 - Enables websites to access a user’s geographical location
 - Uses SQL database to store data offline
 
 [Reference - GFG](https://www.geeksforgeeks.org/difference-between-html-and-html5/)

 #### 2. How do you create a hyperlink in HTML?
 - A basic link is created by wrapping the text or other content inside an `<a>` element and using the href attribute
 - Allows to link documents to other documents or resources, link to specific parts of documents, or make apps available at a web address
 - Any web content can be converted to a link so that when clicked or otherwise activated the web browser goes to another web address

 ```code
 <p>
    I'm creating a link to
    <a href="https://www.mozilla.org/en-US/">the Mozilla homepage</a>.
 </p>
 ```

 #### 3. What is the purpose of the `<alt>` attribute in the `<img>` tag?
 - The alt attribute in the img tag provides a textual replacement for an image when it can't be displayed
 - This is useful for accessibility, as it helps users who can't see the image understand its content and context
  - **Screen readers** - read the alt text to provide information about the image
  - **Text-based browsers** - Users of text-based web browsers can see the alt text
  - **Failed image loads** - alt text is displayed if the image doesn't load for any reason, such as a slow connection, network errors, or content blocking

#### 4. How do you include a comment in HTML?
- To add a comment in HTML, HTML comment tags `<! --` and `-->` were used
- Place the `<! --` tag before the comment and `-->` tag after the comment
- The web browser will ignore anything between the tags and will not display it on the front end. 
- Comments are a good practice for documenting HTML code and making it easier to understand. 
- You can use them to place notifications and reminders in your HTML

#### 5. What are Non-Semantic & Semantic tags in HTML?
## Non-Semantic Tags
 - Tags, such as `<div>` and `<span>`, are the workhorses of web layout
 - They don't tell you anything about their content
   - `<div>` is simply a block-level container
   - `<span>` is an inline container. 
- These tags are used to apply stylings or JavaScript actions to content
## Semantic Tags ##
- Describe the meaning or purpose of the content they consists of
- Providing a clear structure to the webpage by indicating sections like headers, navigation, articles, and footers.
- Key Benefits:
   - **Clarity** - Make HTML code more readable by explicitly stating the role of each content section. 
   - **Accessibility** - Screen readers interpret the page structure with semantic tags, improving accessibility. 
   - **SEO** - Search engines might also consider semantic tags when indexing a webpage, potentially impacting search rankings. 
- Examples:
   - `<article>` - Represents a self-contained piece of content like a blog post or news article
   - `<aside>` - Content that is related to the page but is considered secondary or sidebar-like
   - `<details>` - Creates a disclosure widget in which data shown with toggle option

  ```code
  <details>
   <summary>Details</summary>
   Something small enough to escape casual notice.
  </details>
  ```

   - `<figcaption>` - Represents a caption or legend describing the rest of the contents of its parent
   - `<figure>` -  Represents self-contained content, potentially with an optional caption. Used to refer image, illustration, diagram or code snippet

   ```code
   <figure>
      <img src="/media/cc0-images/elephant-660-480.jpg" alt="Elephant at sunset" />
      <figcaption>An elephant at sunset</figcaption>
   </figure>
   ```

   - `<footer>` - Represents the footer content of a page 
   - `<header>` - Represents introductory content at the top of a page, often including logos and navigation 
   - `<main>` - Contains the primary content of a webpage 
   - `<mark>` - Represents text which is marked or highlighted for reference or notation purposes

   ```code
   <p>Several species of <mark>salamander</mark> inhabit the temperate rainforest of the Pacific Northwest.</p>
   ```

   - `<nav>` - Defines a section containing navigation links 
   - `<section>` - Groups related content within a page
   - `<summary>` - Specifies a summary, caption, or legend for a `<details>` element's disclosure box
   - `<time>` - Represents a specific period in time. It may include the datetime attribute to translate dates into machine-readable format, allowing for better search engine results or custom features such as reminders

   ```code
      <p>The Cure will be celebrating their 40th anniversary on <time datetime="2018-07-07">July 7</time> in London's Hyde Park.</p>

      <p> The concert starts at <time datetime="20:00">20:00</time> and you'll be able to enjoy the band for at least <time datetime="PT2H30M">2h 30m</time>.</p>
   ```

#### 6. How do you create an ordered and unordered list in HTML?

```code
<ol>
    <li>First item</li>
    <li>Second item</li>
</ol>
<ul>
    <li>First item</li>
    <li>Second item</li>
</ul>
```

#### 7. How can you display an image in HTML?

```code
<img src="image.jpg" alt="Description of image" width="300" height="200">
```

#### 8. How do you create a form with text input and a submit button?

```code
<form action="/submit" method="post">
    <input type="text" name="username" placeholder="Enter your name">
    <button type="submit">Submit</button>
</form>
```

#### 9. How do you make text bold or italic in HTML?

```code
<b>This text is bold</b>
<i>This text is italic</i>
```

#### 10. How do you create a hyperlink that opens in a new tab?

```code
<a href="https://example.com" target="_blank">Visit Example</a>
```