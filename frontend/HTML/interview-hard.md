
# Interview - Hard

### Questions
1. [How does the Document Object Model (DOM) relate to HTML?](#1-how-does-the-document-object-model-dom-relate-to-html)
2. [Explain the concept of accessibility in HTML. How to ensure a webpage is accessible?](#2-explain-the-concept-of-accessibility-in-html-how-to-ensure-a-webpage-is-accessible)
3. [How to optimize HTML for SEO (Search Engine Optimization)?](#3-how-to-optimize-html-for-seo-search-engine-optimization)
4. [What is the purpose of the `<template>` tag, and how can it be used?](#4-what-is-the-purpose-of-the-template-tag-and-how-can-it-be-used)
5. [Explain the difference between server-side rendering (SSR) and client-side rendering (CSR) with respect to HTML?](#5-explain-the-difference-between-server-side-rendering-ssr-and-client-side-rendering-csr-with-respect-to-html)
6. [How do you create a responsive image using HTML?](#6-how-do-you-create-a-responsive-image-using-html)
7. [How do you structure a webpage using semantic HTML?](#7-how-do-you-structure-a-webpage-using-semantic-html)
8. [How do you create a modal popup using HTML?](#8-how-do-you-create-a-modal-popup-using-html)
9. [How do you use the `<details>` and `<summary>` elements?](#9-how-do-you-use-the-details-and-summary-elements)
10. [How do you create a custom data attribute and use it in JavaScript?](#10-how-do-you-create-a-custom-data-attribute-and-use-it-in-javascript)

---

### Answers

#### 1. How does the Document Object Model (DOM) relate to HTML?
 - An application programming interface (API) for HTML and XML documents
 - Defines the logical structure of documents and the way a document is accessed and manipulated
 - Represents a logical tree, where each branch ends in a node that contains objects
 - Allows programs to change the document's structure, style, or content
 - JavaScript uses the DOM to
    - Access and change HTML elements
    - Create dynamic HTML
    - Change HTML attributes
    - Change CSS styles
    - React to HTML events

#### 2. Explain the concept of accessibility in HTML. How to ensure a webpage is accessible?
 - Accessibility can be acheived by 
    - Designing webpages that can be used by everyone, including people with disabilities
    - Utilizing proper HTML elements and attributes to ensure content is perceivable, operable, understandable, and robust
    - Allowing users to navigate and interact with the page effectively using assistive technologies like screen readers or keyboard navigation. 
 - **Tips to ensure accessiblility**
    - **Semantic HTML** - Use appropriate HTML tags for their intended meaning (e.g., `<header>`, `<nav>`, `<article>`) to provide structure and context for screen readers. 
    - **Alternative Text (Alt Text)** - For images, always include descriptive "alt" attributes that explain the image content for users who cannot see it. 
    - **Headings** - Use heading tags (`<h1>` to `<h6>`) in a logical hierarchy to structure content and guide navigation for screen reader users. 
    - **Keyboard Navigation** - Design your page so all interactive elements can be accessed and activated solely using the keyboard. 
    - **Color Contrast** - Ensure sufficient color contrast between text and background colors to improve readability for users with visual impairments. 
    - **Form Labels** - Clearly associate labels with form input fields using the for attribute to make it easier for screen readers to understand form functionality. 
    - **ARIA Attributes** - Utilize ARIA (Accessible Rich Internet Applications) attributes to provide additional semantic information about elements, especially for complex interactive components. 
    - **Language Declaration** - Specify the language of the page using the lang attribute on the `<html>` tag to assist screen readers with pronunciation. 
    - **Clear and Simple Language** - Use plain language and avoid jargon to make content understandable for everyone. 
 - **Important Accessibility Considerations**
    - **Screen Readers** - Always design with screen readers in mind, ensuring text is read aloud in a logical order and important information is conveyed through alt text and semantic HTML.
    - **Motor Impairments** - Consider users who may navigate with keyboard only and ensure all interactive elements are accessible via keyboard. 
    - **Cognitive Disabilities** - Use clear and concise language, avoid complex layouts, and provide options for users to adjust font sizes and color schemes. 
    - **Testing and Validation** - Regularly test your website with assistive technologies and use accessibility checkers to identify and address issues.

#### 3. How to optimize HTML for SEO (Search Engine Optimization)?
 - **Title Tags** - Use clear, concise, and keyword-rich titles that accurately describe your page content within the character limit
 - **Meta Descriptions** - Write engaging meta descriptions that summarize your page and entice users to click through from search results
 - **Header Tags (H1, H2, H3)** - Use heading tags to structure your content hierarchically, highlighting important sections with relevant keywords
 - **Semantic HTML Tags** - Employ HTML5 semantic tags like `<header>`, `<nav>`, `<article>`, `<section>`, and `<footer>` to indicate the structure and meaning of your page content
 - **Image Optimization** - Use descriptive file names for images. Add "alt text" to describe the image for accessibility and search engines. Optimize image sizes to improve loading speed
 - **URL Structure** - Create clear and descriptive URLs that include relevant keywords. Avoid long, complex URLs with unnecessary parameters
 - **Canonical Tags** - Use canonical tags to specify the preferred version of a page when dealing with duplicate content
 - **Keyword Placement** - Naturally incorporate relevant keywords throughout your content, including titles, headings, and body text. Avoid keyword stuffing
 - **Internal Linking** - Link to other relevant pages on your website to improve navigation and distribute link authority
 - **Schema Markup** - Consider using schema markup to provide additional context about your content to search engines, potentially enhancing your search result appearance
 - **Robots Meta Tag** - Use the "robots" meta tag to control how search engines crawl and index your pages
 - Important points to remember
    - **Quality Content** - Always prioritize creating high-quality, valuable content that is relevant to your target audience
    - **Mobile Friendliness** - Ensure your website is responsive and optimized for mobile devices
    - **Technical SEO** - Regularly check for broken links, site speed issues, and other technical factors that can impact SEO

#### 4. What is the purpose of the `<template>` tag, and how can it be used?
 - A mechanism for holding HTML fragments
 - A container to hold some HTML content hidden from the user when the page loads
 - Dynamically inserted into the DOM later using JavaScript, essentially acting as a reusable template for generating content on demand, especially when dealing with dynamic web applications
 ```code
 <table id="producttable">
  <thead>
    <tr>
      <td>UPC_Code</td>
      <td>Product_Name</td>
    </tr>
  </thead>
  <tbody>
    <!-- existing data could optionally be included here -->
  </tbody>
</table>

<template id="productrow">
  <tr>
    <td class="record"></td>
    <td></td>
  </tr>
</template>

<script>
    // Test to see if the browser supports the HTML template element by checking
    // for the presence of the template element's content attribute.
    if ("content" in document.createElement("template")) {
    // Instantiate the table with the existing HTML tbody
    // and the row with the template
    const tbody = document.querySelector("tbody");
    const template = document.querySelector("#productrow");

    // Clone the new row and insert it into the table
    const clone = template.content.cloneNode(true);
    let td = clone.querySelectorAll("td");
    td[0].textContent = "1235646565";
    td[1].textContent = "Stuff";

    tbody.appendChild(clone);

    // Clone the new row and insert it into the table
    const clone2 = template.content.cloneNode(true);
    td = clone2.querySelectorAll("td");
    td[0].textContent = "0384928528";
    td[1].textContent = "Acme Kidney Beans 2";

    tbody.appendChild(clone2);
    } else {
    // Find another way to add the rows to the table because
    // the HTML template element is not supported.
    }
</script>
 ```
#### 5. Explain the difference between server-side rendering (SSR) and client-side rendering (CSR) with respect to HTML?
 - **Server-side rendering (SSR)** - The server generates the entire HTML content for a page and sends it to the browser. This is better for SEO-dependent websites with static content. 
 - **Client-side rendering (CSR)** - The browser receives a minimal HTML file and uses JavaScript to render the content dynamically. This is better for web applications that require fast user interactions.

 #### 6. How do you create a responsive image using HTML?

 ```code
 <img src="image.jpg" style="max-width: 100%; height: auto;">
 ```
 #### 7. How do you structure a webpage using semantic HTML?

 ```code
 <header>
    <h1>Website Title</h1>
    <nav>
        <ul>
            <li><a href="#home">Home</a></li>
            <li><a href="#about">About</a></li>
        </ul>
    </nav>
</header>
<main>
    <section id="home">
        <h2>Welcome</h2>
        <p>This is the homepage.</p>
    </section>
    <section id="about">
        <h2>About Us</h2>
        <p>Information about us.</p>
    </section>
</main>
<footer>
    <p>Copyright © 2024</p>
</footer>
 ```

 #### 8. How do you create a modal popup using HTML?

 ```code
 <div id="modal" style="display: none; position: fixed; background: rgba(0,0,0,0.5);">
    <div style="background: white; padding: 20px;">
        <p>This is a modal.</p>
        <button onclick="document.getElementById('modal').style.display='none'">Close</button>
    </div>
</div>
<button onclick="document.getElementById('modal').style.display='block'">Open Modal</button>
 ```

 #### 9. How do you use the `<details>` and `<summary>` elements?

 ```code
 <details>
    <summary>Click to expand</summary>
    <p>This is the expanded content.</p>
 </details>
 ```

 #### 10. How do you create a custom data attribute and use it in JavaScript?

 ```code
 <button data-user-id="12345" onclick="alert(this.dataset.userId)">Click Me</button>
 ```