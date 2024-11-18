
# Interview - Easy

### Questions
1. [How to change the text color of an element?](#1-how-to-change-the-text-color-of-an-element)
2. [How to set a background color for a webpage?](#2-how-to-set-a-background-color-for-a-webpage)
3. [How to make text bold using CSS?](#3-how-to-make-text-bold-using-css)
4. [How to center-align text in CSS?](#4-how-to-center-align-text-in-css)
5. [How to set a border around an element?](#5-how-to-set-a-border-around-an-element)
6. [How to set padding and margin for an element?](#6-how-to-set-padding-and-margin-for-an-element)
7. [How to make an image circular using CSS?](#7-how-to-make-an-image-circular-using-css)
8. [How to use the z-index property to layer elements?](#8-how-to-use-the-z-index-property-to-layer-elements)
9. [How to apply a shadow to an element?](#9-how-to-apply-a-shadow-to-an-element)
10. [How to create a transition effect on hover?](#10-how-to-create-a-transition-effect-on-hover)

---

### Answers

#### 1. How to change the text color of an element?
```code
p { color: red; }
```
#### 2. How to set a background color for a webpage?
```code
body { background-color: lightblue; }
```
#### 3. How to make text bold using CSS?
```code
p { font-weight: bold; }
```
#### 4. How to center-align text in CSS?
```code
h1 { text-align: center; }
```
#### 5. How to set a border around an element?
```code
div { border: 2px solid black; }
```
#### 6. How to set padding and margin for an element?
```code
div {
    padding: 20px;
    margin: 10px;
}
```
#### 7. How to make an image circular using CSS?
```code
img { border-radius: 50%; }
```
#### 8. How to use the z-index property to layer elements?
```code
.foreground {
    z-index: 2;
    position: relative;
}
.background {
    z-index: 1;
    position: relative;
}
```
#### 9. How to apply a shadow to an element?
```code
div { box-shadow: 5px 5px 10px gray; }
```
#### 10. How to create a transition effect on hover?
```code
a {
    color: black;
    transition: color 0.5s;
}
a:hover {
    color: red;
}
```