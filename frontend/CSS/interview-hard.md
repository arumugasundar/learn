
# Interview - Hard

### Questions
1. [How to create a flexbox container to align items horizontally?](#1-how-to-create-a-flexbox-container-to-align-items-horizontally)
2. [How to create a grid layout with three equal columns?](#2-how-to-create-a-grid-layout-with-three-equal-columns)
3. [How to use CSS variables to store reusable values?](#3-how-to-use-css-variables-to-store-reusable-values)
4. [How to create a CSS animation that moves an element?](#4-how-to-create-a-css-animation-that-moves-an-element)
5. [How to make an element responsive using media queries?](#5-how-to-make-an-element-responsive-using-media-queries)
6. [How to use the grid-area property to place items in a grid layout?](#6-how-to-use-the-grid-area-property-to-place-items-in-a-grid-layout)
7. [How to create a custom scrollbar style?](#7-how-to-create-a-custom-scrollbar-style)
8. [How to create a gradient border for an element?](#8-how-to-create-a-gradient-border-for-an-element)
9. [How to hide an element but keep it accessible to screen readers?](#9-how-to-hide-an-element-but-keep-it-accessible-to-screen-readers)
10. [How to create a CSS-only dropdown menu?](#10-how-to-create-a-css-only-dropdown-menu)

---

### Answers

#### 1. How to create a flexbox container to align items horizontally?
```code
.container {
    display: flex;
    justify-content: space-between;
}
```
#### 2. How to create a grid layout with three equal columns?
```code
.grid {
    display: grid;
    grid-template-columns: repeat(3, 1fr);
}
```
#### 3. How to use CSS variables to store reusable values?
```code
:root {
    --main-color: blue;
}
h1 {
    color: var(--main-color);
}
```
#### 4. How to create a CSS animation that moves an element?
```code
@keyframes move {
    from { transform: translateX(0); }
    to { transform: translateX(100px); }
}
div {
    animation: move 2s infinite;
}
```
#### 5. How to make an element responsive using media queries?
```code
@media (max-width: 600px) {
    div {
        width: 100%;
    }
}
```
#### 6. How to use the grid-area property to place items in a grid layout?
```code
.container {
    display: grid;
    grid-template-areas: 
        "header header"
        "sidebar content"
        "footer footer";
}
.header {
    grid-area: header;
}
```
#### 7. How to create a custom scrollbar style?
```code
::-webkit-scrollbar {
    width: 10px;
}
::-webkit-scrollbar-thumb {
    background-color: gray;
}
```
#### 8. How to create a gradient border for an element?
```code
div {
    border: 5px solid transparent;
    border-image: linear-gradient(to right, red, blue) 1;
}
```
#### 9. How to hide an element but keep it accessible to screen readers?
```code
.hidden {
    position: absolute;
    clip: rect(1px, 1px, 1px, 1px);
}
```
#### 10. How to create a CSS-only dropdown menu?
```code
.menu {
    position: relative;
}
.menu:hover .dropdown {
    display: block;
}
.dropdown {
    display: none;
    position: absolute;
    background: white;
}
```
