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

