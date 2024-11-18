
# Interview - Intermediate

### Questions
1. [How do you apply CSS to a specific element with an ID?](#)
2. [How do you create a CSS class and apply it to multiple elements?](#)
3. [How do you change the size of an element using CSS?](#)
4. [How do you use a pseudo-class to style the first child of a list?](#)
5. [How do you set a hover effect for a button?](#)
6. [How do you create a sticky header using CSS?](#)
7. [How do you create a responsive navigation bar?](#)
8. [How do you use the clip-path property to create a custom shape?](#)
9. [How do you use the position property to overlap elements?](#)
10. [How do you create a parallax scrolling effect with CSS?](#)

---

### Answers

#### 1. How do you apply CSS to a specific element with an ID?
```code
#header { background-color: gray; }
```
#### 2. How do you create a CSS class and apply it to multiple elements?
```code
.highlight {
    color: white;
    background-color: blue;
}
```
#### 3. How do you change the size of an element using CSS?
```code
div {
    width: 200px;
    height: 100px;
}
```
#### 4. How do you use a pseudo-class to style the first child of a list?
```code
ul li:first-child { color: green; }
```
#### 5. How do you set a hover effect for a button?
```code
button:hover { background-color: yellow; }
```
#### 6. How do you create a sticky header using CSS?
```code
header {
    position: sticky;
    top: 0;
    background-color: white;
}
```
#### 7. How do you create a responsive navigation bar?
```code
nav {
    display: flex;
    flex-wrap: wrap;
    justify-content: space-around;
}
```
#### 8. How do you use the clip-path property to create a custom shape?
```code
div {
    clip-path: polygon(50% 0%, 100% 100%, 0% 100%);
}
```
#### 9. How do you use the position property to overlap elements?
```code
.box1 {
    position: absolute;
    top: 20px;
    left: 20px;
}
.box2 {
    position: absolute;
    top: 40px;
    left: 40px;
}
```
#### 10. How do you create a parallax scrolling effect with CSS?
```code
.parallax {
    background-image: url('image.jpg');
    background-attachment: fixed;
    background-size: cover;
}
```