
# Interview - Intermediate

### Questions
1. [How does the `<canvas>` element work in HTML5?](#)
2. [What is the difference between `<section>` and `<div>`?](#)
3. [How can you embed audio and video in an HTML document?](#)
4. [Explain the difference between id, name and class attributes in HTML?](#)
5. [What are data attributes, and how can they be used in HTML?](#)

---

### Answers

#### 1. How does the `<canvas>` element work in HTML5?
 - Allows for the dynamic rendering of 2D shapes and bitmap images
 - The HTML `<canvas>` element is used to draw graphics, on the fly, via scripting (usually JavaScript)
 - The `<canvas>` element is only a container for graphics
 - Canvas has several methods for drawing paths, boxes, circles, text, and adding images
 - Insights
    - **Drawing Surface** - Creates a fixed-size drawing surface
    - **Rendering Contexts** - Exposes one or more rendering contexts, which are used to create and manipulate the content shown
    - **Script Access** - Accesses the rendering context and draws on it
    - **Drawing Functions** - Access the area through a set of functions
    - **Size** - Has a width and height set in the markup
    - **Visibility** - CSS can be used to make the canvas visible
    - **Movement** - CSS3 transition properties can be used to move the canvas around
    - **Stylings** - A border, padding, background color, and margins can be added to the canvas
```code
<canvas id="myCanvas" width="200" height="100" style="border:1px solid #000000;"></canvas>
```

#### 2. What is the difference between `<section>` and `<div>`?
## Section ##
 - Element that groups related content into a distinct section of a web page
 - Used to divide a page into sections like chapters or headers, and is more informative for assistive technologies like screen readers
## Div ##
 - Element that groups related elements together for styling or scripting purposes
 - `<div>` does not have any semantic meaning, and is often used for smaller things like containers for presentations

#### 3. How can you embed audio and video in an HTML document?
 - `<audio>` tag is used to embed sound content in a document, such as music or other audio streams
 - `<video>` tag is used to embed video content in a document, such as a movie clip or other video streams
 - `<audio>` & `<video>` tag contains one or more `<source>` tags with different audio sources. The browser will choose the first source it supports
 ```code
 <audio controls>
  <source src="horse.ogg" type="audio/ogg">
  <source src="horse.mp3" type="audio/mpeg">
  Your browser does not support the audio tag.
 </audio>

 <video width="320" height="240" controls>
  <source src="movie.mp4" type="video/mp4">
  <source src="movie.ogg" type="video/ogg">
  Your browser does not support the video tag.
 </video>
 ```

#### 4. Difference between id, name and class attributes in HTML?
 - **Uniqueness** - Only one element on a page can have a particular `id`. 
 - **Multiple usage** - To apply multiple `class` names to a single element. 
 - **Form specific** - The `name` attribute is most relevant when working with form elements

#### 5. What are data attributes, and how can they be used in HTML?
 - Custom attributes that store additional information about HTML elements
 - Used to store data that is associated with a particular element but doesn't have a defined meaning
 - Store extra information, Improve user experience and Communicate with CSS and JavaScript