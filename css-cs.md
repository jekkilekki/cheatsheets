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
color: DarkCyan; = There are 147 predefined color names
color: #ee3e80; | color: #cde; = 6-digit code that shows Red, Green, Blue (2 numbers each - or 1 if both are the same)
color: rgb(100,100,90); = Red, Green, Blue color values (maximum = 255)
color: rgba(100,100,90,0.5); = Red, Green, Blue, Alpha (transparency) color values (0.5 = 50% opaque)
opacity: 0.5; = Sets the transparency of an element (from 0.0 (0% opaque or visible) to 1.0 (100% opaque)
background-color: transparent; = Background color (default is transparent) - can also use names, hex numbers, and rgb
(R) Red; (G) Green; (B) Blue = screen colors | (C) Cyan; (M) Magenta; (Y) Yellow; (K) Black = print colors
(H) Hue = which color; (S) Saturation = amount of gray; (B) Brightness (Photoshop) = amount of black = (L) Lightness (CSS)
background-color: hsl(100,100,90); = (H) = angle (0-360 degrees); (S) = %; (L) = % (0 white; 50 normal; 100 black)
background-color: hsla(100,100,90,0.5); = Hue, Saturation, Lightness, Alpha (transparency)
Tip: Add an extra (plain color) rule (first) for older browsers
Contrast: Low = hard to read; High = easiest to read (except for lots of text); Medium = best for readability of long texts
```

###Text

#####Text Notes

__Font Types__ 

1. Serif = printed (newspaper style) text
2. Sans-serif (without serif) = screen (modern) text
3. `Monospace` = code
4. Cursive = handwriting
5. Fantasy = decorative

__Font Terms__

1. Ascender = ‘h’ height (taller than a capital letter)
2. Cap Height = capital letter height
3. X-Height = height of ‘x’
4. Baseline
5. Descender = below baseline

__Methods to use different fonts__ *(be aware of licensing & commercial vs. personal use)*

| Method                        | Description                                             | Disadvantage                    |
|-------------------------------|---------------------------------------------------------|---------------------------------|
| `font-family:` = Font-stack   | Browsers display special fonts if installed             | (fonts must be installed)       |
| `@font-face:`                 | Tells CSS where to download if not installed            | (can slow page loading)         |
| Service-based `@font-face:`   | Commercial services like TypeKit                        | ($$$)                           |
| Fonts as images               | Screen-readers use `alt` to know what is said           | (can't copy/paste, not 'fonts') |
| `sIFR`                        | Javascript replaces text with Flash movie of the font   | (both must be enabled to work)  |
| `Cufon`                       | Javascript creates an SVG or VML version of the text    | (text can’t change on hover)    |
| Google Fonts                  | Link to a CSS file and font files on Google servers     | (LEAST restrictive - but external calls) |

__Font sizing__

1. `px` = precise control; 
2. `%` = a percent of the default; 
3. `em` = width of letter ‘m’ (relative to parent); 
4. `rem` = ‘m’ relative to HTML root

| 12px scale                                      | 16px scale                                  |
|-------------------------------------------------|---------------------------------------------|
| h1 : 24px; 200%; 1.5em;                         | h1 : 32px; 200%; 2em;                       |
| h2 : 18px; 150%; 1.3em;                         | h2 : 24px; 150%; 1.5em;                     |
| h3 : 14px; 117%; 1.17em;                        | h3 : 18px; 133%; 1.125em;                   |
| body : 12px; 75%; 100%; p : 0.75em; (for IE6/7) | body: 16px; 100%; 100%; p: 1em; (for IE6/7) |

* [REMs vs. EMs](http://css-tricks.com/rems-ems/)
* [There's more to the CSS REM unit than font-sizing](http://css-tricks.com/theres-more-to-the-css-rem-unit-than-font-sizing/)

```css
font-family: “Special font”, “Generic font”, Generic, serif;  /* = Font-stack - end with most generic font */
font-size: 12px; | 200% | 1.3em; | 1.3rem;                    /* = Default size in a browser = 16px */

@font-face { font-family: ‘ChunkFiveRegular’; src: url(‘fonts/chunkfive.eot’); }  /* = Font declaration */
@font-face {                                                  /* = More complicated font declaration */
  font-family: ‘ChunkFiveRegular’; 
  src: url(‘fonts/chunkfive.eot’);                            /* = Embed fonts in the following order */
  src:  url(‘fonts/chunkfive.eot?#iefix’) format(‘embedded-opentype’),  /* = eot (IE 5-9+) */
        url(‘fonts/chunkfive.woff’) format(‘woff’),                     /* = woff (IE 9+; Chrome 6+; Firefox 3.6+) */
        url(‘fonts/chunkfive.ttf’) format(‘truetype’),                  /* = ttf/otf (NOT IE 5-8; NOT iOS<4.2) */
        url(‘fonts/chunkfive.svg#ChunkFiveRegular’) format(‘svg’);      /*  = svg (NOT IE; NOT Firefox) */
}

font-weight: light | medium | bold | black | 100...999;       /* = Font thickness
                                                               *   (Sets text heaviness relative to inherited rules) */
font-style: normal | italic /* (cursive curls) */ | oblique   /* (normal font at an angle)
                                                               *   (If no italic font is available, the normal font will be slanted as oblique) */
font-stretch: condensed | regular | extended                  /* = NOT YET supported by Internet browsers */

text-transform: uppercase; | lowercase; | capitalize;         /* = ALL UPPER, all lower, or Title Style */
text-decoration: none; | underline; | overline; | line-through; | blink;  /* = FYI: blink is annoying */

/* TYPOGRAPHY */
line-height: 1.4em;                                           /* = Leading (vertical space between lines); best practice = use ems to keep relative to text size */
letter-spacing: 0.1em;                                        /* = Kerning (space between each letter) - helpful for all uppercase words; best practice = use ems */
word-spacing: 0.3em;                                          /* = Default gap is set by typeface (around 0.25em) - rare to have to change; best practice = use ems */

text-align: left; | right; | center; | justify;               /* = FYI: left-aligned is best for paragraphs; justified may be weird */
vertical-align: baseline; | sub; | super; | top; | text-top; | middle; | bottom; | text-bottom; 
          /* = Used with inline elements; NOT intended for block elements - can also take length (px or ems) or % of line-height */
text-indent: -9999px;                                         /* = Can either (1) indent the first line (px or ems) OR (2) push text off a page to show a background-image */

text-shadow: 1px 1px 5px #666666;                             /* = Takes x-distance, y-distance, blur amount, color (can take negative x and y values, rgba, hex, names, etc) */ 
```

#####Pseudo Elements
```css
p.intro:first-letter { ... }                    /* = Pseudo-element for the first letter (acts as if an extra code element) */
p.intro:first-line { ... }                      /* = Pseudo-element for the first line */
 
/* THIS order for link pseudo-elements is good: */
a:link { ... }                                  /* = Create rules for unvisited links */
a:visited { ... }                               /* = Create rules for visited links */
a:hover { ... } | input.submit:hover { ... }    /* = Mouseover actions (doesn’t work on touchscreens like iPads) */
input.text:focus { ... }                        /* = Rules for when your cursor is inside a textfield */
a:active { ... } | input.submit:active { ... }  /* = Create rules for activation event */

/* MORE pseduo-elements */
div:before { ... }                              /* = Something to come directly before the element */
div:after { ... }                               /* = Something to come directly after the element */
div:first-child { ... }                         /* = The first of its kind */
div:nth-child(2) { ... }                        /* = The nth number of its kind */
div:last-child { ... }                          /* = The last of its kind */
```

###Boxes
```css
/* = Width/height: 
 * px = most precise; 
 * % = relative to page size; 
 * em = based on size of its text
 */
width: 300px; | 33%; | 3em; 
height: 300px; | 33%; | 3em; 
  min-width: | min-height:                        /* = Smallest box size allowable */
  max-width: | max-height:                        /* = Largest box size allowable */
overflow: hidden; | scroll;                       /* = Hide text that extends outside a box’s borders, OR add a scroll bar for the user */

margin: 10px 10px 0px 0px;                        /* = Space OUTSIDE a box: top right bottom left; (px, %, em) */
  margin: 10px auto 20px auto;                    /* = auto LR margins centers a box (Note: you must set a box width) */
padding: 10px 0px;                                /* = Space INSIDE a box: top + bottom, left + right (Note: padding + margin are added to width) */
box-sizing: border-box;                           /* = keeps margin + padding WITHIN the box width (doesn't stretch) */

display: inline; | block; | inline-block; | none; /* = Show elements inline, as blocks, as blocks floating inline, or none */
visibility: hidden; | visible;                    /* = Hide the element (but leave a blank space) or show it (display:none; removes the element) */
```

#####Borders
```css
border: 1px solid silver;                             /* = Order: border-width, border-style, border-color */
  margin-top: | padding-top: | border-top:            /* = TOP of the box */
  margin-right: | padding-right: | border-right:      /* = RIGHT of the box */
  margin-bottom: | padding-bottom: | border-bottom:   /* = BOTTOM of the box */
  margin-left: | padding-left: | border-left:         /* = LEFT of the box */

border-width: 2px | thin; | medium; | thick;          /* = Assign border width */
border-width: 2px 5px 20px 5px;                       /* = Assign 4 widths (top, right, bottom, left) */
border-color: darkcyan deeppink silver black;         /* = Values in RGB, Hex, or Color Names (top right bottom left) */
border-style: solid; | dotted; | dashed; | double; | groove; | ridge; | inset; | outset; | hidden; | none; 

  border-top-width: | border-top-style: | border-top-color:           /* = TOP border */
  border-right-width: | border-right-style: | border-right-color:     /* = RIGHT border */
  border-bottom-width: | border-bottom-style: | border-bottom-color:  /* = BOTTOM border */
  border-left-width: | border-left-style: | border-left-color:        /* = LEFT border */
```

#####CSS3 Boxes
```css
/**
 * border-image:
 * Takes: (1) URL, (2) where to slice, (3) what to do with edges: stretch; repeat; round; (scales to fit) 
 */
border-image: url(“images/dots.gif”);             /* = Slices bg img into 9 parts for border. */
  -moz-border-image: url(“images/dots.gif”) 11 11 11 11 stretch;  /* = Top, right, bottom, left slices + stretch*/
  -webkit-border-image: url(“images/dots.gif”) 11 11 11 11 round; /* = -moz + -webkit = older Chrome, Firefox, Safari */

/**
 * box-shadow:
 * (1) Horizontal offset, (2) Vertical offset, (3) Blur distance, (4) Spread of shadow (+ = expand; - = contract)
 */
box-shadow: 3px 2px 10px black;
  -moz-box-shadow: inset 0 0 10px #777777;        /* = inset keyword preceding the values = an inner-shadow */
  -webkit-box-shadow: 5px 5px;                    /* = If no blur distance, solid line; If no color = no shadow */

/**
 * border-radius:
 */
border-radius: 5px 10px 5px 10px;                 /* = Rounded corners; top-left, top-right, bottom-right, bottom-left */
  -moz-border-radius: 50%;                        /* = Create a circle */
  -webkit-border-radius: 80px 50px;               /* = Create an ellipse; first value = horizontal, second = vertical */
  border-radius: 1em 4em 1em 4em / 2em 1em 2em 1em;   /* = Strange shape; first #s = all horizontal, second = all vertical */
  
  border-top-left-radius: 10px;
  border-top-right-radius: 30px;
  border-bottom-right-radius: 0px;
  border-bottom-left-radius: 5px;
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
