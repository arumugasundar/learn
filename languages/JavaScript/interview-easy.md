
# Interview - Easy

### Questions
1. [What is the difference between HTML and HTML5?](#what-is-the-difference-between-html-and-html5)
2. [How do you create a hyperlink in HTML?](#how-do-you-create-a-hyperlink-in-html)

---

### Answers

#### 1. What is the difference between HTML and HTML5?
## HTML ##
 - Combination of Hypertext and Markup language
 - **Hypertext** - defines the link between the web pages
 - **Markup Language** - used to define the text document within the tag which defines the structure of web pages
 - Used to annotate text so that a machine can understand it and manipulate text accordingly

 ## HTML5 ##
 - Introduced application programming interfaces(API) and Document Object Model(DOM)
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