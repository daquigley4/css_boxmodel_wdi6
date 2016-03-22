# Intro to CSS and Box Model

[FEWD Slides](http://jrosebud.github.io/)

**Learning Objectives**

- What is CSS?
- What are Selectors?
- What is the Box Model?

## CSS

[Intro to CSS FEWD Slides](http://jrosebud.github.io/lesson02/#/18)

**Cascading Stylesheets**

Provides visual styling rules for specific elements within the document object model (DOM).


## Where styles go

### External stylesheets

The best approach is to include all of your styles through external stylesheets (".css" files) using the `<link>` tag. Add a reset stylesheet first to normalize your environment across browsers!

```
 <link href="reset.css" rel="stylesheet">
 <link href="main.css" rel="stylesheet">
```

### Embedded stylesheets

Styles may be embedded into the HTML document within a `<style>` tag. While this can have its uses, the approach is generally discouraged.

```
 <style>
  body {
    background-color: #ccc;
  }
 </style>
```

### Inline styles

Extremely specific style attributes can be written onto elements within the Document Object Model (DOM). This is the primary method that JavaScript uses to manipulate your presentation. You should avoid using inline styles while composing your base presentation graphics.

```
 <div style="display:none;">I'm hidden.</div>
```

## Selectors

Selectors are used to target elements in the DOM with specific style rules. Selectors may target elements by tag name, class name, id name, or as inline rules applied directly to an element.

### Basic Selectors:

- `tagname`
  - `<p>`, `<div>`
- `.class-name`
  - `.`
- `#id-name`
  - `#`

**HTML:**

```
 <div class="promo" id="pencil-promo">
  <h2>Pencils for sale!</h2>
  <p>For a limited time offer, get yours today!</p>
  <p style="font-size:10px;">Limited time offer, while supplies last.</p>
 </div>
```
**CSS Selectors:**

```
 h2 {
  /* Selects by tag name */
 }

 .promo {
  /* Selects by class name*/
 }

 #pencil-promo {
  /* Selects by id name (maybe you have many promos, but want pencil to be different)*/
 }
```

**Colors:**

  {background-color: rgba(255,0,0,0.3);}   /* red with opacity */

- '0' is invisible

**Fonts & Google Fonts**

- Talk about load time and how to manipulate the link directly.
- On Codepen.io Walk through adding Google fonts both with a head link and with `@` in the css file.

YOU DO:

- Have the students pick a Google font and add it as a link and an `@` in CSS.
- Have them try adding an [animation](https://developers.google.com/fonts/docs/getting_started#Effects) then show how to add an animation to the font.

### Composite Selectors

Selectors may be combined and/or nested. This allows styles to target very specific elements.

- `tag.class-name`
- `.class1.class2`
- `tag#id-name.class-name`
- `.class-name .sub-class`
- `.classname a.class-name`
- group selectors- together with a comma in between them
- `li>a` child selector - targets any elements that are children of an `li`
- `p a` descendant selector - targets and element that is a decendent of a `p`
- `h1+p` adjacent sibling selector - targets the first `p` element after any `h1` elements.
- `h1~p` general sibling selector - any `p` that are siblings of `h1`

There is no technical limit to the nesting of selectors, however, discipline and good judgement while nesting selectors will do you a great service, and improve rendering performance!

```
 div.promo h2 {
  /* Composite selector */
 }
```

[Nesting](http://htmldog.com/guides/css/intermediate/grouping/) Should be used sparingly to make your CSS modular.

###Font - ems, px, %

- px in Explorer isn't enlargable for accessability purposes.
- Ems are relative, 1 em is equal to the current font size of the element in question. By default it's 16 px. You can also put a default font size on the body.
- The most popular method in working with em values is to set the font-size on the body to 62.5%. Because the default browser font-size is 16px, this makes it 10px (without hard-setting it to 10px, which wouldn't cascade).


### Psudo-classes

Special psudo-classes allow us to add additional refinements onto our base selector classes. They target elements based on specialized information in the DOM that simple selectors cannot get... pattern-matching, child-to-parent relationships: nth-child selector. Common psudo-classes include:

**Dynamic**

- `:hover`
- `:focus`
- `:target`

**Structural**

- `:first/last-child`- give the styling to the first child of the parent element
- `:first/last-of-child`- first h2 within the parent element
- `:only-child`- whenever it is the only child, within that section, target it
- `:nth-child(2)`- you have an argument that you can pass into to to create a pattern
- `:nth-child(2n)`- every 2nd element

### Pseudo-element selectors
Differentiate pseudo-element selectors with class selectors.

 - h1 + p::first-line-  double colon is a css3 attribute, and it may not work on older browsers, so you may have to change it back to one colon

- h1 + p::first-letter- font-size: 3em;

## Specificity

[Check out this lesson for more details](https://github.com/ga-students/WDI_ATL_2_Instructors/blob/master/Lessons/css_after_the_intro_class_html5/css-specificity-normalize-html5.md)

Specificity determines what style rules are applied to an element that is targeted by many different style rules. The element's actual computed style is determined by its most *specific* styles.

#### Scoring
Specificity is actually quite easy to calculate:

| selector | value |
|:-- |:----------- |
| **tag** | 1 point  |
| **class**  | 10 points   |
| **id** | 100 points  |
| **inline** | 1000 points   |
| **!important** | 10,000 points   |

So, the net specificity of this selector would be…?:

```
div#features a.slide h3 span
```
This selector is worth **114 points**.

#### Specificity Ties
When two selectors have the same net specificity score, then the last one applied wins. Note that stylesheets are read from top to bottom, and their styles are applied in order… therefore, styles defined lower within your stylesheet will win.

## Basic styles

Some basic element styles:

- **background-color**: #000;
- **background-image**: url("image.jpg");
- **border**: 1px solid #f00;
- **border-radius**: 5px;
- **color**: #FFF;
- **font-family**: Arial, Helvetica, sans-serif;
- **font-size**: 12px;
- **font-style**: italic;
- **font-weight**: bold;
- **line-height**: 2em;
- **list-style**: none;

## Classes, IDs, and The Box Model

[FEWD Box Model](http://jrosebud.github.io/lesson03/#/2)

[Box Model](http://www.vanseodesign.com/css/inline-blocks/)

[Box Model w3schools](http://www.w3schools.com/css/css_boxmodel.asp)


- **border**: 1px solid #f00;
- **display**: block / inline / inline-block / none;
- **height**: 50px;
- **margin**: 10px auto;
- **padding**: 20px 40px;
- **width**: 100px;

### Box attribute order

Box style rules (margin, padding, etc) may include 1-4 values for the different sides. These values are applied as follows:

```
 /* Same on all four sides */
 margin: 20px;

 /* Top-Bottom / Left-Right */
 margin: 20px 40px;

 /* Top / Right / Bottom / Left (clockwise) */
 margin: 10px 50px 50px 40px;
```

##Navigation

[FEWD Nav, Floats, Positioning](http://jrosebud.github.io/lesson04/#/1)

YOU DO: Have the students center their Navs

## Floats

[FEWD Floats Slides](http://jrosebud.github.io/lesson04/#/11)

Floating takes block elements out of standard document flow, and allows them to stack horizontally instead of vertically.

- **float**: left / right / none;
- **clear**: both;
- **overflow**: auto / hidden;

### Wrapping Floats

Because floated content is removed from document flow, you need clear the floated sequence for the parent element to wrap its floated children. There are three main techniques:

#### clear

Add `clear:both;` to an element after the floated content.

```
 <div>
  <div style="float:left;">I'm Floated!</div>
  <div style="clear:both;"></div>
 </div>
```

#### overflow

Add `overflow:auto / hidden;` to the parent element. The overflowed parent will wrap its floated children.

```
 <div style="overflow:auto;">
  <div style="float:left;">I'm Floated!</div>
 </div>
```

#### clearfix

Use a `.clearfix` class on the parent container, and then add a [clearfix implementation](http://css-tricks.com/snippets/css/clear-fix/) into your stylesheet. Clearfix is a widely recognized and accepted practice (albiet, still technically a hack though).

```
 <div class="clearfix">
  <div style="float:left;">I'm Floated!</div>
 </div>
```

## Positioning

[FEWD Slides](http://jrosebud.github.io/lesson04/#/15)

Elements may define a position attribute that determines how they are placed within the document. Absolute positioning breaks the element from document flow, and aligns it to its nearest relative parent.

- **position**: static / relative / absolute / fixed;
- **bottom**: 0;
- **left**: 0;
- **right**: 0;
- **top**: 0;

[W3 Schools Positioning](http://www.w3schools.com/css/css_positioning.asp)

**Static**

- HTML elements are positioned static by default. A static positioned element is always positioned according to the normal flow of the page.
- Static positioned elements are not affected by the top, bottom, left, and right properties.

**Relative**

- A relative positioned element is positioned relative to its normal position. The element is positioned relative to its normal position, so "left:20" adds 20 pixels to the element's LEFT position

**Absolute**

- An absolute position element is positioned relative to the first parent element that has a position other than static. If no such element is found, the containing block is `html`.

**Fixed**

- An element with a fixed position is positioned relative to the browser window, and will not move even if the window is scrolled. Important for parallax.


## Browser rendering differences
- every browser has its own rendering engine, that uses it to parse your code and tell the browser how to display it
    - each engine, which were all developed at different times, have different parsers, preferences and policies that determine how your code is rendered
- four most common
    - Trident- Microsoft developed this, and it is therefore the proprietary engine; IE + AOL
    - Presto- developed by Opera
    - Gecko- open-sourced rendering engine, originally developed by Netscape; firefox + camino
    - Webkit- open source rendering engine, developed by Apple, Google and Nokia- Apple and Google Chrome
- just learn to become able to recognize the differences in how different browsers render web pages

```
div {
    -webkit-transition: ;
    -moz-transition: ;
    -o-transition: ;
}

```

## Control stacking order
- z-index- auto/ integer/ inherit
    - what matters is which value is higher; the higher the value, the higher it is in the stacking order; usually
         based on how many elements you are controlling, and how much control you need
          - highest = first seen/on top
    - if you have two elements with the same number, source order is used, so whatever is the lowest element
         is on top
    - you can use negative values, but it will put your element behind the elements in the normal document flow; almost as if it is hiding
          - ultimately it will be sent below everything except for the initial stacking context- basically will not go
             below the html element
    - every element given a z-index rating is given a new stacking context
- position: absolute
- z-index: 1; (element 1)
- z-index: 3; (element 2)
- z-index: 2; (element 3)







## Pro Tips

1. **All styles go into external CSS files**. Avoid using inline-styles.
2. **Only style using class and tag selectors**. AVOID STYLING IDs.
3. **Avoid !important**. It's a last resort.
4. **Alphabetize your style rules.** You'll avoid clumsy overrides!

---

# Work with Nested Selectors

Style [nested selectors](http://htmldog.com/guides/css/intermediate/grouping/) to build understanding of:

- the box model
- the cascading effect

---

# CSS Reset

- Make all browsers style elements the same by default
- [Eric Meyer reset](http://meyerweb.com/eric/tools/css/reset/)

Note:
start everything at zero.
.
becomes more important when we're doing cross-browser testing
.
bird's-eye view of x-browser, x-device testing and issues

---

# Fashion Blog

- (add both version of starter to repo: with/without markup)
- Expectations
- Getting started
- HINT: use psudo-selectors for first letter of each section.

Note:
Use the DOM tree to modify your boilerplate.

Format markup as best semantically as you can then start styling.

---

# Final Thoughts

<div style="margin: 1em 0">
Multi-column layout can be achieved many ways now:
</div>

- css floats
- ```display: inline-block```
- ```display: flex``` (flexbox)
- canned CSS grid system (Bootstrap)

Note:
Read up. Flexbox will be the norm eventually.
.
Different situations call for different solutions (as always).
.
[flexbox guide](http://css-tricks.com/snippets/css/a-guide-to-flexbox/)

---

# Homework

- Build [Fashion Blog](../../../Week_02_Styling/03_box_model/starter_code/fashion_blog_part1/README.md) Page
- Read about floats
- Read about classes and IDs
- Play around with ```display: inline-block```


# CSS Positioning


##You Do: CSS Positioning  - 10 minutes

####Directions to students:
1. Create an html page called ```index.html``` with an externally linked css stylesheet called ```main.css```
2. Inside your html page create a "container" div holding four divs within.
3. Inside our CSS page, make the container a 500px gray square containing 100px squares within that are red, blue, green, and black.
<br>


####Deliverable:


```html
<div id="container">
    <div id="square1"></div>
    <div id="square2"></div>
    <div id="square3"></div>
    <div id="square4"></div>
</div>
```

```css
#container {
    height: 500px;
    width: 500px;
    background-color: gray;
}
#square1 {
    background-color: red;
    height: 100px;
    width: 100px;
}
#square2 {
    background-color: blue;
    height: 100px;
    width: 100px;
}
#square3 {
    background-color: green;
    height: 100px;
    width: 100px;
}
#square4 {
    background-color: black;
    height: 100px;
    width: 100px;
}
<br><br>

---

##I Do: The CSS Box Model - 5 minutes

*Explain* the CSS Box Model

- Every element in web design is a rectangle.
- Even if you see a circle, it's living within a box.

*Show* the class that this is true by opening up your Chrome Dev Tools and navigating to the Box Model viewer under Elements.

- **Show** the class what happens when we drop this code into our CSS file:



```css
* {
    border: 1px solid red !important;
}
```

*Explain* how the box model affects CSS positioning
*Show* the class how you can change the padding, border, and margin of one of our boxes


<br>

---

##Intro: Static Positioning - 5 minutes


####Directions:

*Explain* the default positioning for all elements is static.
- This means that no positioning has been applied and the elements occurs where they normally would in the document.

```css
background-color: gray;
    position: static;
    height: 500px;
    width: 500px;
```

You rarely explicitly declare `position:static` like this because it is the default.


<br><br>

---

##We Do: Position: Relative - 5 minutes

####Directions:
*Explain* that declaring `position:relative` allows you to position the element top, bottom, left, or right relative to where it would normally occur.

```css
#square1 {
    background-color: red;
    height: 100px;
    width: 100px;
    position:relative;
    top: 0;
    left: 40px;
}
```
<br><br>

---

##We Do: Position: Absolute - 5 minutes

####Directions:

*Explain:* Specifying `position:absolute` removes the element from the document and places it exactly where you tell it to be.

```css
#square1 {
    background-color: red;
    height: 100px;
    width: 100px;
    position:absolute;
    top: 0;
    right: 0;
}
```
<br><br>

---

##We Do: Position:absolute + Position:relative - 5 minutes

####Directions:

*Explain* that if we declare position relative on the parent container, any elements within that parent container will be positioned relative to that parent container.

```
#container {
    background-color: gray;
    position: relative;
    height: 500px;
    width: 500px;
}
#square1 {
    background-color: red;
    height: 100px;
    width: 100px;
    position:absolute;
    top: 0;
    right: 0;
}
```
<br><br>

---


##We Do: Columns - 5 minutes

####Directions:

*Explain* Now that we have the basics of relative and absolute positioning lets create a two column layout by changing the heights of `square1` and `square2` to 200px and absolutely position the two squares like so:

```css
#container {
    background-color: gray;
    position: relative;
    height: 500px;
    width: 500px;
}
#square1 {
    background-color: red;
    height: 200px;
    width: 100px;
    position:absolute;
    top: 0;
    right: 0;
}
#square2 {
    background-color: blue;
    height: 200px;
    width: 100px;
    position: absolute;
    top: 0;
    left: 0;
}
```

**Note** how our "square2" div is positioned to the top left of the container and "square1" to the top right. This was done to illustrate that absolute positioning doesn't care what order the elements appear in your html.

Also, notice how we can't see square3 or square4? They are being covered up by our absolute-positioned "square2" div (remember absolute positioning removes the element from the document).

We can reveal those missing divs by declaring their absolute position in the bottom left and right of our container:

```css
#square3 {
    background-color: green;
    height: 100px;
    width: 100px;
    position: absolute;
    bottom: 0;
    left: 0;
}
#square4 {
    background-color: black;
    height: 100px;
    width: 100px;
    position: absolute;
    bottom: 0;
    right: 0;
}
```

**Point Out:** This works fine when we know the exact sizes of our elements but what if we were building something like a blog and we had text in those columns or surrounding them, we won't always know the exact amount of text or their font sizes. This is where floats can help us.

<br><br>

---

##We Do: Floats - 5 minutes

####Directions:
*Explain* If our element sizes are variable or dynamic we can use floats to allow text/other elements to wrap around the floated element.

####Directions to students:
- To illustrate lets first go to a [favorite ipsum generator](http://http://baconipsum.com) and grab 4 paragraphs of text.
- Now let's venture back to our html page and add this text after the closing tag of our "square2" div and before the opening tag of our "square3" div.

- Your html should like this:

```html
<!DOCTYPE html>
<html>
<head>
    <link rel="stylesheet" type="text/css" href="main.css">
</head>
<body>
    <div id="container">
        <div id="square1"></div>
        <div id="square2"></div>
        (4 paragraphs of ipsum)
        <div id="square3"></div>
        <div id="square4"></div>
    </div>
</body>
</html>
```

- As expected our text falls behind our absolute positioned columns? Now lets make our elements aware of each other with floats.

- Back in our CSS remove the absolute positioning from our "square2" div and replace it with `float:left` .


```css
#square2 {
    background-color: blue;
    height: 200px;
    width: 100px;
    float: left;
}
```

**Note:** Our text is aware that our "square2" div wants to be as left as possible and kindly wraps it in a nice text hug.

<br>

---

##We Do: Floats with Clears - 5 minutes

####Directions:
*Explain:* While floats make other elements aware of their location and get text hugs, clears make other elements aware and are told not to touch.

####Directions to students:
- Lets go back to our CSS and change our "square2" div's positioning from `float:left` to `clear: right`.
    - Clear is saying "I'm not sure how much space I'm going to take but whatever it is clear off my right side" so our text respects its wishes and drops to the line below.

<br>


