#HTML Cheatsheet

![HTML & CSS book](http://ecx.images-amazon.com/images/I/41CRnsnRWhL._AA160_.jpg)

The following are notes from the HTML portion of Jon Duckett's [HTML and CSS book](http://www.htmlandcssbook.com/). 
CSS notes can be found here. 

__Table of Contents__

1. [Head Section](#head)
2. [Page Elements](#page-elements)
3. [Text](#text)
4. [Links](#links)
5. [Images](#images)
6. [Lists](#lists)
7. [Tables](#tables)
8. [Forms](#forms)
  * [Input Types](#input-types)
9. [Video](#video)
10. [Audio](#audio)

__Block Elements:__ (Start on a new line)
* `<h1>, <h2>, <h3>, <h4>, <h5>, <h6>, <p>, <ul>, <ol>, <li>, <div>`

__Inline Elements:__ (Flow in between surrounding text)
* `<a>, <b>, <i>, <em>, <strong>, <span>, <img>`

###Head
```html
<!DOCTYPE html>                                                               = HTML5 Document Type declaration (precedes everything)
<html></html>                                                                 = Begin and end the webpage HTML code (surrounds everything)
<head></head>                                                                 = Before <body> and contains info about the page
<title></title>                                                               = Title of the webpage (shown in browser tab)
<meta name="description" content="Use max 155 character string" />            = Site meta info (site description)
<meta name="keywords" content="comma, separated, word, list" />               = Website meta information (keywords)
<meta name="robots" content="command" />                                      = Search Engines ("noindex" = don’t index; "nofollow" = don’t index my links)
<meta http-equiv="author" content="Author Name" />                            = Define the site author
<meta http-equiv="pragma" content="no-cache" />                               = Prevent browser caching
<meta http-equiv="expires" content="Fri, 04 Apr 2014 23:59:59 GMT" />         = Expiration date (don’t cache after)
<link type="text/css" rel="stylesheet" href="css/style.css" />                = Link to a stylesheet
<script type="text/javascript" href="http://www.link.com/script.js"></script> = Link to a script
```

[Back to Top](#html-cheatsheet)

###Page Elements
```html
<body></body>                   = Everything that’s shown in the browser window
<!-- Comment -->                = Comments
<div></div>                     = Divider (Traditionally used with ids and classes to specify function)
<header></header>               = Header content for a section
<footer></footer>               = Footer content for a section
<nav></nav>                     = Used for primary navigation (sometimes used in the footer also)
<article></article>             = A stand alone piece of content that may be syndicated (i.e. blog post, forum post, or comment)
<aside></aside>                 = For related info, not part of the main content (sidebars, legends, pullquotes)
<section></section>             = Groups related content together, typically with its own heading
<hgroup></hgroup>               = Allows a title and subtitle to be grouped together
id="identifier"                 = Global attribute; used on only ONE element
class="identifier"              = Attribute used on multiple elements

<!--[if lt IE 9]>               = Help older browsers understand the new HTML5 elements                                    
  <script src="http://html5shiv.googlecode.com/svn/trunk/html5.js"></script> 
<![endif]-->
```

[Back to Top](#html-cheatsheet)

###Text
```html
<style></style>                 = Declare CSS styles
<h1></h1>                       = Main Heading
<h2></h2>                       = Subheading (Level 2)
<h3></h3>                       = Subheading (Level 3)
<h4></h4>                       = Subheading (Level 4)
<h5></h5>                       = Subheading (Level 5)
<h6></h6>                       = Subheading (Level 6)
<p></p>                         = Paragraph text
<b></b>                         = Bold text
<strong></strong>               = Strong text (default: bold)
<i></i>                         = Italic text (also used often for Icon Fonts)
<em></em>                       = Emphasized text (default: italics)
<sup></sup>                     = Superscript (useful for: dates, math)
<sub></sub>                     = Subscript (footnotes, chemical formulas)
<span></span>                   = Inline styles
<br />                          = Hard return (line break)
<hr />                          = Horizontal rule
<blockquote></blockquote>       = Pullquotes
<q></q>                         = Inline (short) quotes
<cite></cite>                   = Citation (material, not people; default: italics)
<dfn></dfn>                     = Definition (some browsers default: italics)
<abbr title="Full name"></abbr> = Abbreviations & accronyms
<address></address>             = Address (default: italics; also see: hCards)
<ins></ins>                     = Inserted content (default: underline)
<del></del>                     = Deleted content (default: strikethrough)
<s></s>                         = Strikethrough (no longer relevant but don’t delete)
```

[Back to Top](#html-cheatsheet)

###Links
```html
<a href="http://www.source.com" target="_blank">Title</a> = Hyperlink (Absolute URL) + open link in new window
<a href="index.html">Title</a>                            = Hyperlink (Relative URL; same folder)
<a href="../index.html">Title</a>                         = Hyperlink (Relative URL; parent folder)
<a href="mailto:me@thissite.com">Email</a>                = Send an email (opens the default email client)

<h1 id="anchor">Anchor<h1>                                = Create links mid-page
<a href="#anchor">Go to Anchor</a>
```

[Back to Top](#html-cheatsheet)

###Images
__Rules:__

1. Use the Right format (jpg, gif, png)
1. Use the Right size (prevent distortion/stretching)
1. Use the Right resolution (72 ppi)

__Formats:__

* `.jpg` = Use for: photos (_multi-colored images_)
* `.gif` = Use for: logos, graphics (_flat-colored images + animation;_ overused in the 90s)
* `.png` = Use for: logos, graphics (_flat-colors + best format for semi-opaque (non-straight edge) **transparency**_)
* `.svg` = Scalable Vector Graphics (_logos;_ not yet widespread use)

```html
<img src="images/sourc.jpg" alt="Short description" title="Additional info" /> = Image
<img ... width="200" height="300" />  = Image with width and height specified
<img ... align="right" />             = Floated image (horizontal options: left / right; vertical options: top / middle / bottom)

<figure></figure>                     = Associate an img with its caption (surround <img> + <figcaption>
<figcaption></figcaption>             = Caption for the <img> contained in the <figure> tags
```

[Back to Top](#html-cheatsheet)

###Lists
```html
<ol></ol>                       = Ordered (numbered) lists
<ol start="4"></ol>             = Where to begin numbering
<ol reversed="reversed"></ol>   = Descending order
<ul></ul>                       = Unordered (bulleted) lists
<li></li>                       = List item
<dl></dl>                       = Definition list (a series of terms + dfns)
<dt></dt>                       = Definition term
<dd></dd>                       = Definition data
```

[Back to Top](#html-cheatsheet)

###Tables
```html
<table></table>                 = Table
<th></th>                       = Table header row
<tr></tr>                       = Table row
<td></td>                       = Table data
  colspan="3"                   = Extend <th> or <td> horizontally across (3) cells
  rowspan="2"                   = Extend <th> or <td> vertically across (2) cells
  scope="row" | "column"        = Indicates the scope of <th>
<thead></thead>                 = Contains the headings of the table
<tbody></tbody>                 = Contains the body of the table
<tfoot></tfoot>                 = Contains the footer of the table
```

[Back to Top](#html-cheatsheet)

###Forms
```html
<form id="name"></form>         = Form (id makes it distinct and may also be used by scripts)
  action="http://www.example.com/subscribe.php"   = The page that receives info when submitted
  method="get"                                    = Values are added to the end of the action URL (use: short forms, search, retrieving data)
  method="post"                                   = Values are sent in HTTP headers (use: uploads, long forms, sensitive data, add/delete from database)
<input type="text" name="name" maxlength="30" />  = Input form
  name                          = Identifier for the form control that is sent to the server with the entered info
  maxlength                     = Maximum number of characters allowed in a text field (i.e. 4 for a year)
  value="name"                  = The option the user has selected or input
  checked="checked"             = Which value (if any) should be selected when the page loads
  placeholder="Text string"     = Default text that is shown to the user
<textarea></textarea>           = Extend the <th> or <td> vertically across multiple (2) cells

<select></select>               = A dropdown box
<option></option>               = Similar to <li>, displays the options to choose from (value stored in value; selected = when page loads)
  size="3"                      = Turn the dropdown into a select box displaying specified number of items
  multiple="multiple"           = Allow users to select more than one option using the CTRL key

<button></button>               = More control over buttons (combine text and images)
<label for="fieldname"></label> = Label for a field; for lets you click the label to select the field

<fieldset></fieldset>           = Group form elements together
<legend></legend>               = Used directly after fieldset, captions the fieldset
```

[Back to Top](#html-cheatsheet)

#####Input Types
```html
<input type="text" />           = Text field
<input type="password" />       = Text field with dots for characters
<input type="radio" />          = Radio button
<input type="checkbox" />       = Checkbox
<input type="file" />           = File uploader
<input type="submit" />         = Submit button
<input type="image" />          = Use an image for the submit button
<input type="hidden" />         = Not shown on the page
<input type="date" />           = Submit a date (date selector on new browsers)
<input type="email" />          = Submit an email (data validation on new browsers)
<input type="url" />            = Submit a URL (data validation on new browsers)
<input type="search" />         = Search field
```

[Back to Top](#html-cheatsheet)

###Video 
```html
<script type="text/javascript"  = SWFObject Script
  src="http://ajax.googleapis.com/ajax/libs/swfobject/2.2/swfobject.js">
</script> 
<script type="text-javascript"> 
  swfobject.embedSWF("flash/bird.swf", "bird", "400", "300", "8.0.0"); = Embed Flash with SWFObject
</script>
```
__Above Script:__

1. Location = `"flash/bird.swf"`
2. ID of HTML element to replace = `"bird"`
3. Width / Height
4. Minimum version of Flash player needed = `"8.0.0"`

#####HTML5 Video How To

`<video></video>` = HTML5 tag for Video

1. Convert to Flash or H264
  * Use [Miro Video Converter](www.mirovideoconverter.com) to convert videos
2. Include FLV Player: 
  * [www.osflv.com](www.osflv.com)
  * [www.longtailvideo.com](www.longtailvideo.com))
3. Include Video(s):
  * __WebM__ (Android, Chrome, Firefox, Opera) and 
  * __MP4__ (IE, Safari)
  * Also include Flash video as a fallback for older browsers

```html
<video
  preload="none" | "auto" | "metadata"  = Don’t load until "Played" | Auto-download the video | Just get the metadata
  src="pathtovideo.mp4"                 = Path to video
  poster="img.jpg"                      = Image to use as placeholder until "Played"
  width="300" height="200"              = Specify width & height
  controls autoplay loop >              = Make browser supply its own controls & Play file automatically & Loop the content
<source src="path.mp4" type='video/mp4;codecs="avc1.42E01E, mp4a.40.2"' />  = Replaces src above
<source src="path.webm" type='video/webm;codecs="vp8, vorbis"' />           = Replaces src above (Example 2)
</video>
```

[Back to Top](#html-cheatsheet)

###Audio
```html
<script type="text/javascript"  = SWFObject Script
  src="http://ajax.googleapis.com/ajax/libs/swfobject/2.2/swfobject.js">
</script> 
<script type="text-javascript"> = Embed MP3 with SWFObject
  var flashvars = {};           = A necessary variable before params even though it is empty
  var params                    = {mp3: "audio/test/audio.mp3"}; 
  swfobject.embedSWF("flash/player_mp3_1.0.0.swf", "music-player", "200", "20", "8.0.0", flashvars, params); 
</script> 
```

#####HTML5 Audio How To

`<audio></audio>` = HTML5 tag for Audio

1. Include Players: 
  * [flash-mp3-player.net](flash-mp3-player.net)
  * [musicplayer.sourceforge.net](musicplayer.sourceforge.net)
  * [www.wimpyplayer.com](www.wimpyplayer.com)
2. Include Audio files:
  * __MP3__ (Safari 5+, Chrome 6+, IE9)
  * __OGG__ (Firefox 3.6, Chrome 6, Opera 1.5, IE9)

```html
<audio
  preload="none" | "auto" | "metadata"  = Don’t load until "Played" | Auto-download the audio | Just get the metadata
  src="pathtoaudio.mp3"                 = Path to audio
  width="200" height="20"               = Specify width & height
  controls autoplay loop >              = Make browser supply its own controls & Play file automatically & Loop the content
<source src="audio/test.mp3" />
<source src="audio/test.ogg" />         = Use like <source> for <video> tags above; type attribute is not commonly used
</audio>
```

[Back to Top](#html-cheatsheet)
