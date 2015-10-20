#CSS Cheatsheet

![HTML & CSS book](http://ecx.images-amazon.com/images/I/41CRnsnRWhL._AA160_.jpg)

The following are notes from the CSS portion of Jon Duckett's [HTML and CSS book](http://www.htmlandcssbook.com/). 
HTML notes can be found here. 

__Table of Contents__

###Notes

###HTML
```css

```

###CSS Selectors
```css

```

###CSS Attribute Selectors
```css

```

###Color
```css

```

###Text

#####Text Notes

```css

```

#####Pseudo Elements
```css

```

###Boxes
```css

```

#####Borders
```css

```

#####CSS3 Boxes
```css

```

###Lists
```css
ul { list-style-type: none;                       /* = Unordered lists bullet points */
                      disc; (●)
                      circle; (○)
                      square; (■) 
}
ol { list-style-type: none;                       /* = Ordered lists bullets */
                      decimal; (1 2 3) 
                      decimal-leading-zero; (01 02 03)
                      lower-alpha; (a b c) 
                      upper-alpha; (A B C) 
                      lower-roman; (i. ii. iii.) 
                      upper-roman; (I II III) 
} 
ul {  list-style-image: url(“images/star.png”);   /* = Use image for a bullet; This (and above rules) also work on <li> */
      list-style-position:  outside;              /* = Outside (default): the marker sits to the left of the text; 
                            inside;               /* = Inside: inside the box of text */
}
ol { list-style: circle inside; }                 /* = Shorthand rule to specify list-style-type, list-style-image, or list-style-position in any order */
```

###Tables

__Generally:__

1. Give cells padding to improve readability
2. Distinguish headings `<th>` to make them easier to read (try `uppercase, bold, letter-spacing, background-color`, etc)
3. Shade alternate rows to keep lines of the table looking clean
4. Align numbers with `text-align: right;` to easily distinguish large and small numbers

```css
table { ... }                                       = Style tables with most Box and Text CSS rules (also :hover) 
table { empty-cells: show; | hide; | inherit; }     = Show or hide the borders around empty cells
table { border-spacing: 5px 10px; }                 = Set space between cells: Takes horizontal value, vertical value
table { border-collapse: collapse; | separate; }    = Collapse borders to single border (previous rules ignored) or separate
```

###Forms

__Generally:__

1. text inputs and textareas, 
2. submit buttons, 
3. labels to line up the controls nicely

__Aligning Form Controls:__ 

1. align `<label>`s to the right with `padding-right`, and 
2. align `<input>`s to the left with a consistent `width`
3. Also assign cursor styles to add helpful information for users in places they expect to see it (i.e. help for a `<dfn>`)
  * `cursor: auto; | crosshair; | default; | pointer; | move; | text; | wait; | help; | url(“cursor.gif”);`

```css
input { ... }                                       = Style with Box and Text styles as seen previously
input:focus { background-color: blue; }             = Change the background-color when it is being used
input:hover { background-color: gray; }             = Change the background-color when it is being hovered over
input[type=submit] { ... }                          = Input types inherit styles from <input> unless specified 
input[type=text] { ... } 
input[type=url] { ... } 
input[type=email] { ... } 
input[type=tel] { ... } 
input[type=number] { ... } 
input[type=color] { ... } 
input:not([type=submit]):not([type=file]) { ... }   = Style all <input>s EXCEPT submit and file
fieldset { ... }                                    = Style fieldset to show the edges of a form with Box and Text styles
legend { ... }                                      = Style legend to show what information is required in the fieldset with Box and Text styles
```

###Layout

| Types of document layouts                                             | Advantages            | Disadvantages             |
|-----------------------------------------------------------------------|-----------------------|---------------------------|
| 1. Fixed width layout: Designs don’t change size; measurements in px  | Accurate positioning  | Gaps, built for 1 screen  |
| 2. Liquid layout: Designs stretch or contract with browser; uses %    | Tolerant to user      |Too wide/squashed text     |
| 3. Responsive layout: Various styles “turn on” at various sizes       | Control every exp     | Harder to design          | 
| 4. Layout Grids: 960 Grid System, 12 / 16-col (may use CSS Framework) | Done for you          | Bloated; use their classes|

__Frameworks:__ 
* Grid: http://www.960.gs 
* Responsive: http://www.unsemantic.com
* Twitter Bootstrap: 
* Zurb Foundation: 

`.col1, .col2, .col3 { width: 200px; float: left; margin: 10px; }` = Multi-column layouts use `<div>`s
 
__Types of document flow:__

1. `position: static;` = Normal flow: block elements appears on a new line, (this is default, so no need to specify it)
2. `position: relative;` = Relative positioning: pushes element in relation to where it WOULD have been (doesn’t affect others)
3. `position: absolute;` = Absolute positioning: box is taken OUT of normal flow and positioned in relation to its parent
4. `position: fixed;` = Fixed positioning: a type of absolute positioning - sets the element in relation to the browser window
5. `float: left; | right; | none;` = Floating elements: float elements to the left or right of others (requires: width)
  * `top: 5px; right: 10px; bottom: 20px; left: 9px;` = Offset properties to indicate how far to move it (px, %, em)
  * `z-index: 10;` = Stacking content based on the z-axis (boxes with a higher z-index appear on top)
  * `clear: left; | right; | both; | none;` = Allow no element within the same box to touch specified side

* __Problem:__ Parents of floated elements may collapse to 0 pixels tall
* __Solution:__ Originally, add a clear at the bottom; Recently, pure CSS: `overflow: auto; width: 100%;`
 
__Common Screen sizes:__

```css
320x240px | 320x224px     = Smallest handphone sizes
960x640px                 = iPhone4 
1334x750px | 1920x1080px  = iPhone6 (retina)
1024x768px                = iPad 2 
2048x1536px               = iPad 3 (retina)
1280x800px                = 13” MacBook 
2880x1800px               = 15” MacBook (retina)
2560x1440px               = 27” iMac 
5120x2880px               = 27” iMac (retina)
```

###Images

`.thumb, .small, .medium, .large, .align-right, .align-left, .align-none` = Assign classes for consistent styling

```css
img {
  width: 33%;                   /* = Size images in % or px or auto */
  height: auto;                 /* = Size images */
  float: left | right | none;   /* = Position images */
  display: block;               /* = Images are inline by default, this will allow you to center them */
  text-align: center;           /* = On the element containing the image OR */
  margin: 0 auto;               /* = On the image itself */
}
```

#####Background Images

* High-contrast imgs = photos (no good for bg); 
* Low-contrast = OK for bg; OR overlay text with a semi-transparent background

```css
#background {
  background-image: url(“images/img.png”);                                              /* = Set a background image */
  background-repeat: repeat; | repeat-x; | repeat-y; | no-repeat;                       /* = Repeat all, horizontally, vertically, or none */
  background-attachment: fixed; | scroll;                                               /* = Background stays in the same position on the page OR moves as you scroll */
  background-position: left top; | center top; | right top;                             /* = Background position within its containing element */
    left center; | center center; | right center; | left bottom; | center bottom; | right bottom; 
  background: #ffffff url(“images/img.png”) no-repeat top right;                        /* = Color, URL, Repeat, Attachment, Position */
  background: url(“img1.jpg”) no-repeat top left, url(“img2.jpg”) no-repeat top right;  /* = CSS3 = multiple imgs OK */
}
```

#####Image Sprites

__Sprites__ = using a SINGLE image (with multiple image parts) and using CSS to allow only one part to show at any time

```css
a.button {                                                /* = Button */
  height: 36px; 
  background-image: url(“button-sprite.jpg”); 
  display: inline-block; 
}

a#class-name {                                            /* = Standard button state */
  width: 210px; 
  background-position: 0px 0px; 
} 

a#class-name:hover { background-position: 0px -40px; }    /* = Hovered button state (touchscreens can’t show) */
a#class-name:active { background-position: 0px -80px; }   /* = Active button state (touchscreens will show) */
```

#####Gradients
```css
#gradient {           /* = Specify a gradient with fallbacks */ 
  background-color: #66cccc;                                                                /* fallback color */
  background-image: url(“images/fallback-gradient.png”);                                    /* fallback image */
  background-image: -moz-linear-gradient(#336666, #66cccc);                                 /* Firefox 3.6+ */
  background-image: -webkit-gradient(linear, 0% 0%, 0% 100%, from(#66cccc), to(#336666));   /* Saf4, Chrome1 */
  background-image: -webkit-linear-gradient(#336666, #66cccc);                              /* Safari 5.1+, Chrome 10+ */ 
  background-image: -o-linear-gradient(#336666, #66cccc);                                   /* Opera 11.10+ */ 
  height: 150px; 
  width: 300px; 
}
```

###Helpful Websites

* CSS testing: BrowserCam.com, BrowserLab.Adobe.com, BrowserShots.org, CrossBrowserTesting.com
* CSS bugs: PositionIsEverything.net, QuirksMode.org
* Color picking tool: colorschemedesigner.com
* Color contrast tool: www.snook.ca/technical/colour_contrast/colour.html
* Fonts: fontsquirrel.com, fontex.org, openfontlibrary.org, typekit.com, kernest.com, fontspring.com
* Font Format Generator: www.fontsquirrel.com/fontface/generator
* CSS Form Styling Consistency (radio buttons, checkboxes, etc): http://formalize.me
* Web Developer Toolbar (Firefox + Chrome): www.chrispederick.com/work/web-developer (similar to “Inspect Element”)
* Frameworks: Grid: www.960.gs, blueprintcss.org, lessframework.com, developer.yahoo.com/yui/grids
* Frameworks: Responsive: http://www.unsemantic.com
