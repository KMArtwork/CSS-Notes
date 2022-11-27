# CSS Notes

Like every language, CSS has its own syntax/rules for how its written. CSS can be written either as a *ruleset* or as *inline style*.


## Rulesets 

```
p {
        color:blue;
   }
```
	
A ruleset is what we call the css written above, it defines how certain HTML elements will be styled. Each ruleset has a specific syntax that must be applied, beginning with a *selector*, followed by the *declaration block* which contains the style *declaration*. Once we have our HTML written, our *rulesets* exist in a separate .css document. 

The **selector** specifies which HTML that will be styled, in this case its the "p" at the very beginning.

The **declaration block** is everything thats inbetween the curly brackets { } and the brackets themselves.

The **declaration** is the name for the *property and value pairs* which style the selected element.
 
**Property** refers to the first part of the pair which signifies the visual characteristic of the element being modified while **value** is the second part of the pair which defines the property.


## Inline Style & Inline Stylesheets

> <p style='color:blue;'>Hello, World!</p>

Inline style is what we call it when we write our CSS styling directly in the HTML document. Above, there is the `<p>` *opening tag* followed by the `style` *attribute* and then the *declaration* of the property/value pair `color:blue`.

If we want to add multiple style attributes to an HTML element we can keep on by separating each property/value pair with a semicolon.

> <p style='color:blue; font-size: 16px;'>Lorem Ipsum</p>

**Most of the time inline styling is not used but every now and then its needed so its good to know about.**

There is also **internal stylesheets** which are similar to inline style in that the CSS exists inside the html document, however a style sheet is typically created and exists in the <head> element of the HTML, contained between the <style> opening and closing tags. 

Whatever CSS stylization is created in the internal stylesheet will apply to the whole HTML document. This part must be written in CSS syntax even though it exists inside the HTML document.


## External Stylesheets 

These stylesheets are created outside of the HTML and exist as their own .css document. i.e. "style.css" This helps to maintain readability in both the HTML and CSS documents and is typically the standard way that CSS stylization is handled. However, having both an HTML and CSS document by themselves is not enough. 

**The two must be linked so that the HTML knows to style the webpage according to the CSS style.**

We do this by using the `<link>` element which must be placed inside the `<head>` of the HTML file. `<link>` is self closing and requires an `href` attribute and a `rel` attribute.
 
`href` is like the anchor element, and the value is the path/address to the CSS file. The path can either be an external one or an internal. (https://www.url.com/stylesheet.css OR /style.css)
	
`rel` describes the relationship betwen the HTML and the CSS. i.e. if we are linking a stylesheet, the value should be "stylesheet"

> <link href="path-goes-here.css" rel="stylesheet"/>


## Selectors

These are how we *select* what HTML element we target with our CSS style. Selectors can also be referred to as tag name or element selector. Selectors do not have angle brackets <> surrounding them like their HTML counterparts. i.e. text { } VS <text></text>.

The asterisk `*` can be used as a *universal selector* to select elements of any/all types.


## Targeting Class

HTML tags also have attributes that can be targeted and styled. For example if we had 

> <p class="brand">Shoe Company</p>

We could target the class attribute by writing our CSS as follows

> .brand {color:teal;}

If we want to assign *multiple class* attribute values to a HTML element we can just do so by seperating each class value with a space i.e. 

<p class="brand title">Shoe Company</p>


## Targeting IDs

But what if we want to target one single specific HTML element with CSS? We can do that with the id attribute. In contrast to class, which can have multiple values, an elements' ID can only have a single value and be used once per page.

When we target something using the id, the CSS must be prepended by a `#`, i.e.

> <h1 id="first-title">First Title</h1>

would be targeted by using the CSS

> #first-title {color:red;}


## Attribute Selector

We can also target HTML elements by their attribute, for example making all links (aka. href) a certain color or font size. Attributes can targeted by putting the attribute name, or the selector, in between two square brackets `[ ]`.

> [href] {color:magenta;} 

We can get even more specific by using the syntax

> type[attribute*=value]

Which selects any element that contains an instance of the value.

For instance, if we had multiple images on our webpage, we could set anchors with hyperlink references that end in .com to be one color and any that end in .gov as a different color. You could also target specific words

> a[href*='.com'] {color:green;}

> a[href*='.gov'] {color:red;}


## Psuedo-Class

We use pseudo-classes for things like greying out the submit button before all the forms are filled in, or changing a link from blue to purple once its been clicked on. They can be attached to any selector and is always written as a colon followed by a name. For example:

> p:hover {background-color:lime;}

Syntax: 

> selector:pseudo-class {property:value;}


## Classes and IDs

HTML elements have types, classes, and ids which we can target and style with CSS. 

CSS also has its own classes and IDs that serve their own purposes.
	
*Classes* are meant to be reused over many elements.

For example, you have 2 different <h1> elements. One needs to be bold and blue, the other needs to be bold and red. Instead of writing 2 seperate rules in the CSS document for each <h1> element, you could write a .green, .blue, and .bold rule in CSS. Then give one headline class="bold green" and the other class="bold blue".

*IDs* are meant to style one specific element. **They override the styles of classes and should be used sparringly to spare yourself the headache.**


## Specificity

Specificity refers to the order/hierarchy in which CSS styles are displayed. Its best practice to style elements using the lowest degree of specificity possible so that the styling is easy to maintain and make changes to.

IDs > Classes > Type

IDs are most specific and therefore will override and style rules created for Classes and Types.


## Chaining

When writing CSS rules, you may require an HTML element to have two or more CSS selectors at the same time. This is done by combining multiple selectors, which we refer to as *chaining*. 

for instance if we had multiple <h1> elements but one or more of them had had the `class` attribute with the `special` value, i.e.

> <h1 class='special'>

Then, in CSS, we would write

> h1.special { ... }

And this would *only* target the HTML elements of <h1> with the class "special". If a <p> paragraph element also had a class of "special" the rule would NOT apply.


## Descendant Combinator

This is how we target HTML elements that are nested inside of other HTML elements. Think the Parent / Child relationship of HTML code. Descendant Combinators are used to target the child, or "descendant", html.

If we have an ordered list `<ol class="main-list">` parent with list item `<li>` children, we can target the list items by writing in CSS:

> .main-list li { ... }

Note that the `.` before main-list is necessary if we are targeting a class. If we were to be targeting a whole element nested inside of another element we could type:

> li h4 { ... }

This would select any <h4> elements that were nested inside of a list item `<li>`


## Multiple Selectors

We can separate selectors with a comma if we want to target two or more separate elements and apply the same style to all of them

Instead of writing 

```
h1 {font-family:Georgia} 

.menu {font-family:Georgia}
```

We could write 

> h1, .menu {font-family:Georgia;}

____________________________________________________________________________________________________________________


VISUAL RULES of CSS

There are some fundamental CSS VISUAL RULES that we need to be aware of



FONT FAMILY, or the more technical term "typeface" is how we can specifiy what kind of font we want to use across the entire web page.

h1 {font-family:Georgia;} 

Would set any <h1> element to be rendered with the Georgia font. 
	-The Font being used must be installed on the user's computer or downloaded with the site
	-WEB SAFE FONTS are a group of fonts that most browsers and operating systems already have
		-Best to use web safe fonts so that your web pages are correctly displayed across as much PCs as possible
		-If the font name is two or more words, put the font in quotes (single or double), i.e. {font-family:"Courier New";}


FONT SIZE can be set by writing
h1 {font-size:18px;}

FONT WEIGHT can be changed by setting the value of font-weight to either bold or normal.
h1 {font-weight: bold;}


TEXT ALIGNMENT can be set with the property text-align.
h1 {text-align: center;}

	-By default all text aligns to the left side of whatever container it is in. We can set the value of the text-align property to either LEFT, CENTER, or RIGHT and also JUSTIFY which spaces out text so that it aligns with both the left and right side of the parent element.


COLOR & BACKGROUND COLOR can be set by using the color and background-color properties and then assigning them a value.
h1 {color:red; background-color: blue;}


OPACITY can be changed with the opacity property and can be set from a value of 0 to 1, where 1 is fully visibile and 0 is invisible.
h1 {opacity:0.5;}

BACKGROUND IMAGE is used when we want to use an image as the background of an element instead of just a color.
.main-banner {background-image:url('https:www.url.com)}
	
	-The value of the background-image property will be a url, which can either be an internal or an external link (i.e. somewhere in your project or somewhere on the internet). If it is internal it must be linked with a RELATIVE FILE PATH.
.main-banner {background-image: url('images/mountains.jpg');


IMPORTANT can be applied to specific declarations instead of full rules. It overrides ANY STYLE no matter how specific it is and as a result this feature should be used very sparingly. However, sometimes we will need to use it, for example when we work with multiple stylesheets. The syntax is
p {color:blue !important;}

____________________________________________________________________________________________________________________

THE BOX MODEL

Browsers load HTML elements with default positions and values, this can lead to unexpected user experiences and also limit the views you can create. 

When you change the background color of an element somtimes there are unintended consequences, like the color stretching beyond the bounds of the element. All elements are "living" inside of a box. This is the box we refer to in the box model. When you change the background color of an element you change the entire bg color of the box.
	-Boxes have DIMENSIONS, BORDERS, PADDINGS, MARGINS

The CONTENT of the box is surroudned by the PADDING, which is surrounded by the BORDER, and then surrounded by the MARGIN


HEIGHT and WIDTH by default are set to hold the raw contents of the box. We can modify this by adding height and width properties in our CSS rules and then assigning them values.
.class {height:300px; width: 600px;}


BORDERS are a line that surrounds an element, like a frame on a painting. Borders can have width, style, and color attributes.
	-WIDTH can be set by defining a pixel amount of using the values thin, medium, or thick.
	-STYLE can be set to one of ten otions, none, dotted, and solid.
	-COLOR can be set using hexcodes or built in keywords like red, blue, violet, etc.
	-A borders default values are medium, none, color ; where color is the current color of the element. If width, style, or color are not given values in the CSS ruleset, then the default values will be used instead.


BORDER RADIUS can be used to soften/round the corners of the box/border. For instance if we set the value of the border-radius to 5px then each corner will have a radius of 5px, as in the corners will match the curvature of a circle with a radius of 5px.

If we want to make a border that is a perfect cricle, we set the size of the box to be equal in height and weight, and then set the value of the border-radius to 50%.

{...
height: 60px; weight 60px; border: 2px solid red; border-radius: 50%;
...}



PADDING is the space between the borders of the box and the content. Padding is like the space between the frame and the picture. We can modify the space by using 
selector {padding: 10px;}

	PADDING SHORTHAND
	-4 VALUES We can also get more specific by using padding-top, padding-bottom, padding-left, padding-right properties and assigning them values OR we can write ...{padding: 5px 6px 7px 8px;}. This targets the padding in a clockwise direction, starting at the top. (5 top, 6 right, 7 bot, 8 left)

	-3 VALUES can be used if we want to pad the left and right with the same value, but have different top and bottom values. The first value targets the top, second value targets left and right, and third targets with bottom.

	-2 VALUES will pad the top and bottom with te first value and pad te left and right with the second.


MARGIN is the space directly outside of the box and the rules can be modified exactly the same as PADDING and PADDING SHORTHAND.

AUTO lets you center the content. For example

{...
width: 400px;
margin: 0 auto;
...}

This sets the top and bottom margin to 0px and then automatically adjusts the left and right so that the element stays centered within its containing element. In order to center and element we must set a width, otherwise it will be automatically set to the full width of its containing element, like <body> for example. Its impossible to center an element that takes up the full width of the page since the width can change due to display &/o browser window size. Setting the width to 400 in the previous code example will cause the div to center within a containing element that is greater than 400px wide.


MARGIN COLLAPSE refers to how overlapping vertical margin space works. When there are two separate elements (boxes) next to each other (left and right) the margin space between the two boxes is sum of both elements margins. So if box-a has a margin of 10px and box-b has a margin of 10px then the total horizontal space between them will be 20px.

If there are two elements next to each other vertically (top/bottom) then the TOTAL VERITCAL SPACE between them will be whatever the largest margin value is. For example if Box A is on top of Box C, and A has a bottom margin value of 10px and Box C has a top margin value of 30px, the vertical distance between the two elements would be 30px. This is MARGIN COLLAPSE.


You can also set the min and max width elements because web pages can be viewed thru displays of differing screen sizes. 
If the max height is set too low/small for the content, then the content will spill outside of the box.


OVERFLOW is how we control when content spills outside of its box. By using the overflow property, we can assign a few values such as hidden, scroll, and visible.
	-HIDDEN hides content that spills outside of the box
	-SCROLL will add a scroll bar so that the rest of the content can be viewed by scrolling
	-VISIBLE will allow the content to be visible outside of the box. This is the default option.


RESETTING DEFAULTS

All major web browsers have default stylesheets the use in absence of an external one. These are known as USER AGENT STYLESHEETS, in this case the term "user agent" is a technical term for the browser.

Because of these user agent stylesheets, sometimes they interfere with your work as a web developer. Many devs choose to reset these default values so they can work with a clean slate, we do this by creating the CSS rule

* {margin: 0; padding: 0;}

This is often the first rule in an external stylesheet. Note that these values are set to 0 and not 0px, when these properties are set to 0 they do not require a unit of measurement.


VISIBILITY of elements can be controlled with the visiblity property. We can set the value to hidden, visible, and collapse - which are all kinda self explanatory.

Note that even if the visiblity is set to hidden, users can still find it using inspect element and viewing the source code in their browser. Furthermore, the page will only hide the content, the space will still be reserved on the web page although it will be blank.

____________________________________________________________________________________________________________________


CHANGING THE BOX MODEL

The box model does have an awkwardl imitartion regarding the box dimensions. If we have a box with a border of 1px, padding of 10px and a height & width of 200px by 300px, the height and width of the box are now 222px by 322px because of the 10px padding on either side and the 1px border as well. 

To prevent this from happening, we can control the box-sizing property of the CSS rule. By default its value is content-box; this is affected by the previously mentioned problem.

We can reset the entire box model and assign a new value: border-box

* {box-sizing: border-box;}

Will set all boxes to be of the border-box value. This keeps the height and width at a fixed value and the border thickness and padding values will be included inside of the box, meaning no overall dimensions of the box will change.

____________________________________________________________________________________________________________________


BOX MODEL IN DEV TOOLS (INSPECT ELEMENT)

Google chrome has a thing called DevTools that web devs can use to see the box around every element of a web page. This can be incredibly useful for developers to figure out where content begins and ends.

On windows we can use CTRL+SHIFT+I to open the dev tools. Alternatively we can use F12 or also clicking the 3 vertical dot menu>more tools>developer tools

For example, open the DevTools, make sure elements is selected at the top, and in then click on Computed in the next section. This will show the element and when you hover over each part (content, padding, border, margin) it will be highlighted on the web page. If you know exactly what element you want to inspect, you can right click directly on the element in the webpage and click on Inspect Element and the DevTool will automatically take you to where that HTML code is located in the Inspect Element area.

You can also change the values by double clicking on the value in the Computed seciton and typing a new number. Note that this change is only temporary and does not override how everyone else experiences the webpage on their own browser. Also, if a borders property alue is set to - initially, and you change it to a number, the changes will not take effect as these values must be first set in the CSS rule sheet.


When using DevTools to check/proof read a web page, we can quickly create a border around all elements using DevTools. First select the HTML declaration in the elements pane <html...>, then in the styles pane, click on the plus icon to add a new rule, and add the rule 
* {border:1px solid red;}
Which will give every element a 1px red border that quickly helps you see the layout and content of a webpage.

____________________________________________________________________________________________________________________


FLOW OF HTML by default, the HTML elements of a webpage will render from left to right, top to bottom, in the same order that they exist in the document. This is called FLOW.


CSS not only controls how HTML elements are styled, but can also control where they are positioned.  Properties such as position, display, z-index, float, and clear are some basic properties for adjusting positions of HTML elements in the browser.


POSITION property controls the default position of an element. It can have the value of static, relative, absolute, fixed, or sticky. Default value is static.

RELATIVE places the element in a position that is relative to its default static position

If we declare the position value as relative, we still need to specifiy where the element shoould be positioned on the page. We do this by accompanying the position declaration with one or more of the OFFSET PROPERTIES, top, bottom, left, &/o right.
	-Top moves the element down from the top
	-Bottom moves the element up from the bottom
	-Left moves the element away from the left side (towards the right)
	-Right mvoes the element away from the right side (towards the left)
These values can be set as pixels, ems, or percentages, among others. These offset properties WILL NOT WORK if the value of the position property is static.


ABSOLUTE makes it so that all other elements on the page will ignore the element with the absolute position value and act as if it is not present on the page. The element will be positioned relative to its closest positioned parent element, while offset properties can be used to determine the final position from there. When an element is set to absolute, the element will scroll with the rest of the document when the user scrolls.


FIXED will fix the elemtn to a specific position on the page regardless of user scrolling. Set the value to fixed and accompany it with offset properties. For example, if we give the <nav> box a fixed position property, then it will stay at the top of the screen even when the user scrolls down/up.


Static and Relative keeps the element flowing with the rest of the document, while Absolute and Fixed prevent the element from flowing with the document. 


STICKY keeps an element flowing as the user scrolls but will STICK to a specified position as the page scrolls further.

{...position:sticky; top: 240px;}

Will keep the position at 240px from the top until it reaches the its correct place in the parent element and then will "unstick"


Z INDEX is how we order things from front to back. When elements overlap each other it can be difficult to read/consume, so we use z-index to determine which elements have priorty (i.e. when overlapped, which elements will appear "on top/in front" and which elements will appear "on bottom/behind" each other). The value is set with an integer and by default all elements have a value of 0. If one element has a z-index of 1, and the other has a z-index of 0, the element with the value of 1 will appear in front of the other element.


INLINE DISPLAY

Inline elements such as <em>, <strong> and <a> only take up as much space necessary to display their conent. The height and width cannot be specified in the CSS document. Inline elements have a box that wraps tightly around the content.

By using the INLINE property on elements that are not inherently inline, we can apply the same style/effect to them.

h1 {display: inline;}

The browser will render <h1> elements on the same line as other inline elements immediately before or after them (if there are any).


BLOCK-LEVEL ELEMENTS are not displayed on the same line as the content around them. These elements fill the entire width of a page by default. but their width property can also be set. Unless otherwise specified, the height will automatically be set to whatever height is needed to fit the content.

Elements like heading elements <h1> - <h6>, <p>, <div>, and <footer> are all block level elements.


INLINE-BLOCK elements combine feature of inline and block elements. THey can appear next to each other and we can specify their dimensions using the width & height properties. Images are the best example of default inline-block elements. If we have three separate <div class="rectangle"> ... </div> elements, by default they would render vertically. However if we use the CSS styling:

.rectangle {display: inline-block; width 200px; height 300px;} 

The boxes will be rendered inline (next to each other horizontally) with the set height and width values.

(quick notes: INLINE elements appear next to each other/on the same line but CANNOT have their height and width properties set. BLOCK elements are not displayed on the same line and CAN have their width and height properties set. INLINE BLOCK allows elements to ahve their height and width properties set AND appear on the same line as teh other elements, provided they have neough space)


FLOAT can be used to most the elemtn as far left or as far right as possible in the container. As opposed to giving it an exact position using offset properties. Float is commonly used for wrapping text around an image, note however that moving elements left or right for layout purposes is better suited for tools like CSS gridbox and flexbox which well learn about later.

The float property is often set either using the value of left or right. This works for static or relative positioned elements. Floated elements MUST HAVE A WIDTH specified, otherwise the element will assume the full width of its containg element and changing the float value will not yield any visible results.

Float can be used to affect multiple elements at once, however when multiple elements are floated and htye have different hiehgts it can affect the layout of hte page. Specifically, elements can "bump" into each other and not allow other elements to properly move left or right.

CLEAR property specifies how elements should behave when they bump into each other on the page. The value can be left, right, both, or none.
	-LEFT prevents the left side of the element from touching any other element within the same containing element.
	-RIGHT prevents the right side of the element from touching
	-BOTH prevents left and right side from touching other lemeents
	-NONE the element CAN touch either side

____________________________________________________________________________________________________________________


COLORS can be definied using keywords, RGB, or HSL, and also HEX color codes. We can change both the color (foreground) and background-color of an element.

KEYWORDS use vaues like "red", "blue", "violet".

RGB and HSL use 3 values to represent the Red Green and Blue or Hue Saturation and Lightness. 
	-{color: rgb (23, 45, 23);
		These numbers must be between 0 and 255.
	-(color: hsl (255, 150, 100);
		The first number HUE must be set between 0 and 360 which represents the angle on a color wheel.
		The second number SATURATION must be between 0 and 100% and represents how intense/rich/vibrant the color is.
		The last number is LIGHTNESS and must be between 0 and 50%. 50% is "normal", 0 is dark(black) and 100 is light(white).

HEX color codes use a # symbol and a combination of 6 letters &/o numbers
	-If a hex color code has triple repeaeting double characters, for example #BB44FF, it can be shortened down to #B4F



OPACITY & ALPHA

Colors can also have an opacity or alpha value. We can do this by using rgba or hsla instead of rgb or hsl. This means we also have to include a fourth value in the declaration which must be between 0 and 1.

We can also add alpha values to hex color codes. If using a 6 digit hex code, add 2 extra digits at the end representing the percentage of opacity. These additional hex digits can range from 00 (transparent) to FF(opaque). Think about how alpha masks in photoshop work. Everything that is in black is masked out and everything that is in white is still visible. Therefore, when the hex alpha is 00, the value is "black" and the visibility is "0/fasle". When the hex alpha is FF, the value is "white" and the visiblity is "1/true".

Alpha values cannot be applied to named colors, only RGB, HSL, or HEX color codes. However there is a named color keyword for 0 opacity, and that is "transparent" which is equivalent to rgba (0,0,0,0), and can be written like:
{color:transparent;}

____________________________________________________________________________________________________________________


TYPOGRAPHY

FONT FAMILY can be set by using the font-family property.
h1 {font-family: arial;}

If the name of the font is multiple words, the font name must be encapsulated by quotes.
h1 {font-family: 'Times New Roman';}

WEB SAFE FONTS refer to the group of fonts that are widely used by major web browsers and are safe to use on web pages without having to worry about wether or not the font will show. If the webpage uses a non-web safe font, the font must be installed on the device that is viewing the web page.


FALLBACK FONTS & FONT STACKS can be used as a way to create contingency plans for if certain text don't work.
h1 {font-family: Caslon, Georgia, 'Times New Roman';}

This is whats called a FONT STACK. The browser will first try to use Caslon, and if unable to do that will use Georgia, and then if unable to use that will use Times New Roman. It usually contains a list of similar-looking fonts. Each subsequent font after the first (Caslon) is a FALLBACK FONT.

SERIF and SANS-SERIF refers to typefaces that have little tail thingies or not. SERIF refers to the little tail things and SANS-SERIF do not have it. Think of Times New Roman vs Arial. Serif fonts are typically used in print, like newspapers, while Sans Serif is typically used for digital media. 

SERIF and SANS-SERIF are always keyword values that can be added as the final fallback font if nothing else in front of the stack are available.
h1 {font-family: Caslon, Georgia, 'Times New Roman'; serif;}

In the above example, if any of the first 3 fonts arent available, the browser will use whatever serif font is available on the system.


FONT WEIGHT property can be specified with either keywords of numerical values. Keywords are BOLD, NORMAL (default value), LIGHTER (one font weight lighter than elements parent value), or BOLDER (one font weight bolder than element's parent).

Numerical values can always be used from 1 to 1000, with 1 being the lightest and 1000 boldest. A weight of 400 is equal to normal, 700 is equal to bold. Its best practice to use increments of 100. Its important to knwo that not all fonts can be assigned numeric font weight, and not all numeric font weights are available to all fonts. Its best to look up the font and see what avaialbe font weight values are available.


FONT STYLE is a way to italicize text. By default the font-style is of a normal value.
h1 {font-style: italic;}


TEXT TRANSFORMATION is a way to make the text either all uppercase or all lowercase.
h1 {text-transform: uppercase;}


LETTER-SPACING is used to set the horizontal spacing between the individual characters in an element. Its not common to have to do this but sometimes it can be useful. This property cna take length values in units, such as 2px or 0.5em.
p {letter-spacing: 2px;}

WORD-SPACING works in a similar way and sets the horizontal spacing between each word. It takes values as units such as 3px or 0.5em;
h1 {word-spacing: 2px;}

LINE HEIGHT can be specificed to set how tall we want each line containing our text to be. Line height can be a unitless number, such as 1.2 or a unit value such as 12px, 5%, or 2em. Typically, a unitless number such as 1.2 is preferable, because it is responsive based on current font size. In other words, if the line height value is 1.2, it will automatically adjust if the font size is changed.
p {line-height: 14.}

TEXT ALIGNMENT, aligns text to its parent element.
p {text-align: justify;}


WEB FONTS are different than web safe fonts. Web fonts allow you to to <link> a font from something like Google Fonts or Adobe Fonts, in your HTML documents. You can also used paid fonts from font distributors like fonts.com by downloading them and hosting them with the rest of your site's files. You can create a @font-face ruleset in your CSS stylesheet to link to the relative path of the font file.

Both techniques allow you to go beyond the sometimes "traditional" apperance of web safe fonts.

For Example, if we use Google Fonts, after we find the font that we want to use, a <link> element will be automatically generated. We can then add that element to our <head> element of HTML, and then use that font in our CSS styling.

Fonts can also be added using the @font-face ruleset in your CSS stylesheet, isntead of the <link> element in your HTML document. Downloaded fonts come in a few file formats such as OTF(OpenType Font), TTF (TrueType Font), WOFF(Web Open Font Format) WOFF2(Web Open Font Format 2). The different formats are a progression of standards for how fonts will work with different browsers, with WOFF2 being the most progressive. Its a good idea to unclude TTF, WOFF, and WOFF2 with your @font-face rule to ensure compatibility on all browswers.

When you download the font files to your computer, its a good idea to make sure you generate additional file types for the same font. For example, if we are downloading the Roboto font, by default it will be a .TFF file. We should also generate a .WOFF and .WOFF2 version of the ROBOTO font as well.

When you have all the files you need, move them to a folder inside your website's working directory and you're ready to use them in a @font-face ruleset, for example:

@font-face {
	font-family: "MyParagraphFont";
	src: url('fonts/Roboto.woff2') format('woff2'),
	src: url('fonts/Roboto.woff') format('woff'),
	src: url('fonts/Roboto.ttf') format('truetype'),
}

It's recommended to define the @font-face ruleset at the top of your CSS stylesheet. When you use a downloaded font you can set the name of the font to a custome name, in the above exmaple it is "myparagraphfont". The src property contains 3 values, each specifiying the relative path to the font file and its format. The order of the different formats is important because our browswer will start at the top of the list and search until it finds a font format it supports. Once the @font-face rule is defined, you can use your custom named font on your style sheet, for example:

p {font-family: "myparagraphfont", sans-serif;}

____________________________________________________________________________________________________________________

# Flexbox

Previously, we learned about the box model of CSS display and the many tools and properties we can manipulate to position elements on a webpage. Flexible Box Layout, or *Flexbox*, is a tool that greatly simplifies how to position elements.

There are two important components to a flexbox layout: *flex containers* and *flex items*.

**Flex Containers** 

Flex containers are elements on a page that *contain* flex items. All direct child elements of a flex container are **flex items**. The distinction is important because there are some properties that apply to flex containers and some properties that apply to flex items.

To designate an element as a flex container set the element's `display` property to `flex` or `inline-flex`. Once an element is designated as a flex container, there are several properties we can use to specify how its children behave, some of the basic ones are:

1. `justify-content`
2. `align-items`
3. `flex-grow`
4. `flex-shrink`
5. `flex-basis`
6. `flex`
7. `flex-wrap`
8. `align-content`
9. `flex-direction`
10. `flex-flow`

Flexbox is an elegant tool that makes it easy to address positioning issues that may have been difficult before.

## display: flex

Any element can be a flex container. Flex containers are helpful tools for creating websites that respond to changes in screen sizes. Child elements of flex containers will change size and location in response to the size and position of their parent container.

```
div.container {
  display: flex;
}
```

In the example above, all divs with the class container are flex containers. If they have children, the children are flex items. A div with the declaration display: flex; will remain block level â€” no other elements will appear on the same line as it. However, it will change the behavior of its child elements. Child elements will not begin on new lines.

## inline-flex

When we give a div - a block level element - the `display: flex` property, it remains a block level element. But what if we want multiple flex containers to display inline with each other? 

If we **did not** want div elements to be block-level elements, we would use `display: inline;` However, flexbox provides the `inline-flex` value for the `display` property which allows us to create flex containers that are also inline elements.

```
<div class='container'>
  <p>Iâ€™m inside of a flex container!</p>
  <p>A flex containerâ€™s children are flex items!</p>
</div>
<div class='container'>
  <p>Iâ€™m also a flex item!</p>
  <p>Me too!</p>
</div>
```
```
.container {
  width: 200px;
  height: 200px;
  display: inline-flex;
}
```

In the examples above, there are two container divs. Without a declared width property, each div would stretch the entire width of the page. The paragraphs within each div would also display on top of each other because paragraphs are block-level elements.

If we declare `display: inline-flex`, the divs will display inline with each other if the page is wide enough. Notice that in the example above, the size of the flex container is set. Currently, the size of the parent container will override the size of its child elements. If the parent element is too small, the flex items will shrink to accommodate the parent containerâ€™s size.

```
<div class='container'>
  <div class='child'>
    <h1>1</h1>
  </div>
  <div class='child'>
    <h1>2</h1>
  </div>
</div>
```
```
.container {
  width: 200px;
}
 
.child {
  display: inline-flex;
  width: 150px;
  height: auto;
}
```
In the example above, the .child divs will take up more width (300 pixels) than the container div allows (200 pixels). The .child divs will shrink to accommodate the containerâ€™s size.

## justify-content

By default, when we have a flex or inline-flex container, all of the child elements (flex items) move toward the upper left corner of the parent container. We can change this and specify *how* flex items spread out from left to right along the *main axis*

To position the items from left to right, we use a property called `justify-content`

```
.container {
  display: flex;
  justify-content: flex-end;
}
```
In the example above, we set the value of justify-content to flex-end. This will cause all of the flex items to shift to the right side of the flex container. Here are some commonly used values for the `justify-content` property:

+ `flex-start` : all items to be positioned in order starting from the left of the parent container with no extra space between or before them
+`flex-end` : all items will be positioned in order, with the last item starting on the right side of the parent container with no extra space between or before them.
+`center` : all items will be positioned in order, in the center of the parent container, with no extra space before, between, or after them.
+`space-around` : items will be positioned with equal space before and after each item, resulting in double the space between elements
+`space-between` : items will be positioned with equal space between them, but no extra space ebfore the first or after the last elements.

"No extra space" meaning that margins and borders will be respected, but no more space (than what is specified in the style rules for the particular element) will be added between elements. The size of each individual flex item is not changed by this property.

## align-items

It is possible to align flex items vertically within the container with the `align-items` property.

```
.container {
  align-items: baseline;
}
```
In the example above, the align-items property is set to baseline. This means that the baseline of the content of each item will be aligned. Below are some common values used for the `align-items` property:

+``flex-start`` : all elements will be positioned at the top of the parent container.
+``flex-end`` : all elements will be positioned at the bottom of the parent container.
+``center`` : the center of all elements will be positioned halfway between the top and bottom of the parent container.
+``baseline`` : the bottom of the content of all items will be aligned with each other.
+``stretch`` : if possible, the items will stretch from top to bottom of the container (this is the default value; elements with a specified height will not stretch; elements with a minimum height or no height specified will stretch).

These values tell the elements how to behave along the *cross axis* of the parent container, which stretches from top to bottom.

You might be unfamiliar with the min-height and max-height properties, but you have used height and width before. min-height, max-height, min-width, and max-width are properties that ensure an element is at least a certain size or at most a certain size, but we will cover that a bit further ahead.

## flex-grow

We previously learned that all flex items shrink proportionally when the flex container is too small. Howver, if the parent container is *larger than necessary* then the flex items will **not** stretch by default.

The `flex-grow` property allows us to specify if items *should* grow to fill a container and also which items should grow proportionally, more-or-less, than others.

```
<div class='container'>
  <div class='side'>
    <h1>Iâ€™m on the side of the flex container!</h1>
  </div>
  <div class='center'>
    <h1>I'm in the center of the flex container!</h1>
  </div>
  <div class='side'>
    <h1>I'm on the other side of the flex container!</h1>
  </div>
</div>
```
```
.container {
  display: flex;
}
 
.side {
  width: 100px;
  flex-grow: 1;
}
 
.center {
  width: 100px;
  flex-grow: 2;
}
```

In the example above, the `.container` div has a display value of `flex`, so its three child divs will be positioned next to each other. If there is additional space in the `.container` div (in this case, if it is wider than 300 pixels), the flex items will grow to fill it. The `.center` div will stretch twice as much as the `.side` divs. For example, if there were 60 additional pixels of space, the `center` div would absorb 30 pixels and the `side` divs would absorb 15 pixels each.

**If a max-width is set for an element, it will not grow larger than that even if there is more space for it to absorb.**

Everything in the previous sections were properties that are declared on flex containers, however this property is declared on flex items.

## flex-shrink

Just as `flex-grow` property proportionally stretches flex items, the `flex-shrink` property can be used to specify which elements will shrink and in what proportions.

You may have noticed that flex items will shrink even if the property is not declared, that is because by default the value `flex-shrink` is `1`. However, flex items *do not grow* unless the `flex-grow` property is declared because the default value is `0`.

```
<div class='container'>
  <div class='side'>
    <h1>I'm on the side of the flex container!</h1>
  </div>
  <div class='center'>
    <h1>I'm in the center of the flex container!</h1>
  </div>
  <div class='side'>
    <h1>I'm on the other side of the flex container!</h1>
  </div>
</div>
```
```
.container {
  display: flex;
}
 
.side {
  width: 100px;
  flex-shrink: 1;
}
 
.center {
  width: 100px;
  flex-shrink: 2;
}
```
In the example above, the `.center` div will shrink twice as much as the `.side` divs if the `.container` div is too small to fit the elements within it. If the content is 60 pixels too large for the flex container that surrounds it, the `.center` div will shrink by 30 pixels and the outer divs will shrink by 15 pixels each. Margins are unaffected by `flex-grow` and `flex-shrink`.

Keep in mind, minimum and maximum widths will take precedence over `flex-grow` and `flex-shrink`. As with `flex-grow`, `flex-shrink` will only be employed if the parent container is too small or the browser is adjusted.

## flex-basis

In the previous two exercises, the dimensions of the divs were determined by heights and widths set with CSS. Another way of specifying the width of a flex item is with the `flex-basis` property. This allows us to specify the width of an item before it stretches or shrinks.

```
<div class='container'>
  <div class='side'>
    <h1>Left side!</h1>
  </div>
  <div class='center'>
    <h1>Center!</h1>
  </div>
  <div class='side'>
    <h1>Right side!</h1>
  </div>
</div>
```
```
.container {
  display: flex;
}
 
.side {
  flex-grow: 1;
  flex-basis: 100px;
}
 
.center {
  flex-grow: 2;
  flex-basis: 150px;
}
```

## flex

We can use the `flex` *property* to provide a convenient and simple way to specify the `flex-grow`, `flex-shrink`, and `flex-basis` properties in one line.

Note that the `flex` *property* is different than the `flex` *value* used for the `display` property

```
.big {
  flex: 2 1 150px;
}
 
.small {
  flex: 1 2 100px;
}
```

In the example above, we use the `flex` property to declare the values for `flex-grow`, `flex-shrink`, and `flex-basis` with one line, in that order. 

If we want to only give a value for grow and shrink, but not basis we can just write:

```
.big {
 flex: 2 1;
}
```

Where the first value represents the grow, and the second represents the shrink.

We can also declare a value for grow and basis by writing:

```
.small {
  flex: 1 20px;
}
```

Note that there **is no way** to set shrink and basis using 2 values.

## flex-wrap

Sometimes, we donâ€™t want our content to shrink to fit its container. Instead, we might want flex items to move to the next line when necessary. This can be declared with the `flex-wrap` property. The `flex-wrap` property can accept three values:

1. `wrap` â€” child elements of a flex container that donâ€™t fit into a row will move down to the next line

2. `wrap-reverse` â€” the same functionality as `wrap`, but the order of rows within a flex container is reversed (for example, in a 2-row flexbox, the first row from a `wrap` container will become the second in `wrap-reverse` and the second row from the wrap container will become the first in `wrap-reverse`)

3. `nowrap` â€” prevents items from wrapping; this is the default value and is only necessary to override a wrap value set by a different CSS rule.

```
<div class='container'>
  <div class='item'>
    <h1>We're going to wrap!</h1>
  </div>
  <div class='item'>
    <h1>We're going to wrap!</h1>
  </div>
  <div class='item'>
    <h1>We're going to wrap!</h1>
  </div>
</div>
```
```
.container {
  display: inline-flex;
  flex-wrap: wrap;
  width: 250px;
}
 
.item {
  width: 100px;
  height: 100px;
}
```

In the example above, three flex items are contained by a parent flex container. The flex container is only 250 pixels wide so the three 100 pixel wide flex items cannot fit inline. The `flex-wrap: wrap`; setting causes the third, overflowing item to appear on a new line, below the other two items.

The `flex-wrap` property is declared on flex *containers*.

## align-content

Now that elements can wrap to the next line, we might have multiple rows of flex items within the same container. Previously, we learned to use the `align-items` property to space flex items from the top to the bottom of a flex container. `align-items` is for aligning elements within a single row. If a flex container has multiple rows of content, we can use `align-content` to space the rows from top to bottom.

Here are some commonly used `align-content` values:

+`flex-start` : all rows of elements will be positioned at the top of the parent container with no extra space between.
+`flex-end` : all rows of elements will be positioned at the bottom of the parent container with no extra space between.
+`center` : all rows of elements will be positioned at the center of the parent element with no extra space between.
+`space-between` : all rows of elements will be spaced evenly from the top to the bottom of the container with no space above the first or below the last.
+`space-around` : all rows of elements will be spaced evenly from the top to the bottom of the container with the same amount of space at the top and bottom and between each element.
+`stretch` : if a minimum height or no height is specified, the rows of elements will stretch to fill the parent container from top to bottom (default value).

```
<div class='container'>
  <div class='child'>
    <h1>1</h1>
  </div>
  <div class='child'>
    <h1>2</h1>
  </div>
  <div class='child'>
    <h1>3</h1>
  </div>
  <div class='child'>
    <h1>4</h1>
  </div>
</div>
```
```
.container {
  display: flex;
  width: 400px;
  height: 400px;
  flex-wrap: wrap;
  align-content: space-around;
}
 
.child {
  width: 150px;
  height: 150px;
}
```

In the example above, there are four flex items inside of a flex container. The flex items are set to be 150 pixels wide each, but the parent container is only 400 pixels wide. This means that no more than two elements can be displayed inline. The other two elements will wrap to the next line and there will be two rows of `divs` inside of the flex container. The `align-content` property is set to the value of `space-around`, which means the two rows of divs will be evenly spaced from top to bottom of the parent container with equal space before the first row and after the second, with double space between the rows.

Note that the `align-content`property is declared on **flex containers**

## flex-direction

Flex containers have two axes, a *main* axis and a *cross* axis, think of these like an x and a y axis. By default, the main axis is horizontal (x) and the cross axis is vertical (y).

The main axis is used to position flex items with the properties: `justify-content`, `flex-wrap`, `flex-grow`, `flex-shrink`

While the cross axis is used to position flex items with the properties: `align-items` and `align-content`. 

However, the main and cross axis are interchangable and we can switch them by using the `flex-direction` property. By using `flex-direction: column;` the flex items will be ordered vertically instead of horizontally.

```
<div class='container'>
  <div class='item'>
    <h1>1</h1>
  </div>
  <div class='item'>
    <h1>2</h1>
  </div>
  <div class='item'>
    <h1>3</h1>
  </div>
  <div class='item'>
    <h1>4</h1>
  </div>
  <div class="item">
    <h1>5</h1>
  </div>
</div>
```
```
.container {
  display: flex;
  flex-direction: column;
  width: 1000px;
}
.item {
  height: 100px;
  width: 100px;
}
```
Using the code above, the five divs will be positioned in a vertical column. They *could* fit in a horizontal row, however the `column` value tells the browser to stack the divs on top of one another as opposed to side by side.

Remember that because these divs are now on the cross axis, properties like `justify-content` will not behave the way they did in the previous examples.

`flex-direction` can accept four values:

+ row : elements will be positioned from left to right across the parent element starting from the top left corner (default).

+row-reverse : elements will be positioned from right to left across the parent element starting from the top right corner.

+column : elements will be positioned from top to bottom of the parent element starting from the top left corner.

+column-reverse : elements will be positioned from the bottom to the top of the parent element starting from the bottom left corner.

Remember that the `flex-direction` property is declared on **flex containers**

## flex-flow

Just like the shorthand `flex` property, the shorthand `flex-flow` property is used to decalre both `flex-wrap` and `flex-direction` properties in one line.

```
.container {
  display: flex;
  flex-flow: column wrap;
}
```
The first value of the `flex-flow` property is the value for `flex-direction` while the second is the `flex-wrap` value. 

Remember that the `flex-flow` property is declared on **flex-containers**

## Nested Flexboxes

So far we have only covered multiple flex containers on the same line, but it is also possible to put flex containers inside one another.

```
<div class='container'>
  <div class='left'>
    <img class='small' src='#'/>
    <img class='small' src='#'/>
    <img class='small' src='#' />
  </div>
  <div class='right'>
    <img class='large' src='#' />
  </div>
</div>
```
```
.container {
  display: flex;
  justify-content: center;
  align-items: center;
}
 
.left {
  display: inline-flex;
  flex: 2 1 200px;
  flex-direction: column;
}
 
.right {
  display: inline-flex;
  flex: 1 2 400px;
  align-items: center;
}
 
.small {
  height: 200px;
  width: auto;
}
 
.large {
  height: 600px; 
  width: auto;
}
```
Above, we have a div with three smaller images that display from top to bottom on the left of the page (`.left`). There is also a div with one large image that will display on the right side of the page (`.right`). The left div has a smaller `flex-basis` but stretches to fill more extra space while the right div has a larger `flex-basis` but stretches to fill less extra space.

Both divs are flex items *and* flex containers. The *items* have properties that dictate how they will be positioned in the parent container and how their flex item children will be positioned inside of them.


## Summary

Flexbox is a versatile tool to help position your elements in a more fluid and *flexible* layout.

1. `display: flex` changes an element to a block-level container with flex items inside of it.
2. `display: inline-flex` allows multiple flex containers to appear inline with each other.
3. `justify-content` is used to space items along the main axis.
4. `align-items` is used to space items along the cross axis of a single row.
5. `flex-grow` is used to specify how much space (and in what proportions) flex items absorb along the main axis.
6. `flex-shrink` is used to specify how much flex items shrink and in what proportions along the main axis.
7. `flex-basis` is used to specify the initial size of an element styled with `flex-grow` and/or `flex-shrink`.
8. `flex` is used to specify `flex-grow`, `flex-shrink`, and `flex-basis` in one declaration.
9. `flex-wrap` specifies that elements should shift along the cross axis if the flex container is not large enough.
10. `align-content` is used to space multiple rows along the cross axis.
11. `flex-direction` is used to specify the main and cross axes.
12. `flex-flow` is used to specify `flex-wrap` and `flex-direction` in one declaration.
13.Flex containers can be nested inside of each other by declaring `display: flex` or `display: inline-flex` for children of flex containers.
