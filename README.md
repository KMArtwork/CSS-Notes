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

``` <p style='color:blue;'>Hello, World!</p> ```

Inline style is what we call it when we write our CSS styling directly in the HTML document. Above, there is the `<p>` *opening tag* followed by the `style` *attribute* and then the *declaration* of the property/value pair `color:blue`.

If we want to add multiple style attributes to an HTML element we can keep on by separating each property/value pair with a semicolon.

``` <p style='color:blue; font-size: 16px;'>Lorem Ipsum</p> ```

**Most of the time inline styling is not used but every now and then its needed so its good to know about.**

There is also **internal stylesheets** which are similar to inline style in that the CSS exists inside the html document, however a style sheet is typically created and exists in the <head> element of the HTML, contained between the <style> opening and closing tags. 

Whatever CSS stylization is created in the internal stylesheet will apply to the whole HTML document. This part must be written in CSS syntax even though it exists inside the HTML document.


## External Stylesheets 

These stylesheets are created outside of the HTML and exist as their own .css document. i.e. "style.css" This helps to maintain readability in both the HTML and CSS documents and is typically the standard way that CSS stylization is handled. However, having both an HTML and CSS document by themselves is not enough. 

**The two must be linked so that the HTML knows to style the webpage according to the CSS style.**

We do this by using the `<link>` element which must be placed inside the `<head>` of the HTML file. `<link>` is self closing and requires an `href` attribute and a `rel` attribute.
 
`href` is like the anchor element, and the value is the path/address to the CSS file. The path can either be an external one or an internal. (https://www.url.com/stylesheet.css OR /style.css)
	
`rel` describes the relationship betwen the HTML and the CSS. i.e. if we are linking a stylesheet, the value should be "stylesheet"

``` <link href="path-goes-here.css" rel="stylesheet"/> ```


## Selectors

These are how we *select* what HTML element we target with our CSS style. Selectors can also be referred to as tag name or element selector. Selectors do not have angle brackets <> surrounding them like their HTML counterparts. i.e. text { } VS <text></text>.

The asterisk `*` can be used as a *universal selector* to select elements of any/all types.


## Targeting Class

HTML tags also have attributes that can be targeted and styled. For example if we had 

``` <p class="brand">Shoe Company</p> ```

We could target the class attribute by writing our CSS as follows

``` .brand {color:teal;} ```

If we want to assign *multiple class* attribute values to a HTML element we can just do so by seperating each class value with a space i.e. 

``` <p class="brand title">Shoe Company</p> ```


## Targeting IDs

But what if we want to target one single specific HTML element with CSS? We can do that with the id attribute. In contrast to class, which can have multiple values, an elements' ID can only have a single value and be used once per page.

When we target something using the id, the CSS must be prepended by a `#`, i.e.

``` <h1 id="first-title">First Title</h1> ```

would be targeted by using the CSS

``` #first-title {color:red;} ```


## Attribute Selector

We can also target HTML elements by their attribute, for example making all links (aka. href) a certain color or font size. Attributes can targeted by putting the attribute name, or the selector, in between two square brackets `[ ]`.

``` [href] {color:magenta;} ```

We can get even more specific by using the syntax

``` type[attribute*=value] ```

Which selects any element that contains an instance of the value.

For instance, if we had multiple images on our webpage, we could set anchors with hyperlink references that end in .com to be one color and any that end in .gov as a different color. You could also target specific words

``` a[href*='.com'] {color:green;} ```

``` a[href*='.gov'] {color:red;} ```


## Psuedo-Class

We use pseudo-classes for things like greying out the submit button before all the forms are filled in, or changing a link from blue to purple once its been clicked on. They can be attached to any selector and is always written as a colon followed by a name. For example:

``` p:hover {background-color:lime;} ```

Syntax: 

``` selector:pseudo-class {property:value;} ```


## Classes and IDs

HTML elements have types, classes, and ids which we can target and style with CSS. 

CSS also has its own classes and IDs that serve their own purposes.
	
*Classes* are meant to be reused over many elements.

For example, you have 2 different `<h1>` elements. One needs to be bold and blue, the other needs to be bold and red. Instead of writing 2 seperate rules in the CSS document for each `<h1>` element, you could write a .green, .blue, and .bold rule in CSS. Then give one headline `class="bold green"` and the other `class="bold blue"`.

*IDs* are meant to style one specific element. **They override the styles of classes and should be used sparringly to spare yourself the headache.**


## Specificity

Specificity refers to the order/hierarchy in which CSS styles are displayed. Its best practice to style elements using the lowest degree of specificity possible so that the styling is easy to maintain and make changes to.

IDs > Classes > Type

IDs are most specific and therefore will override and style rules created for Classes and Types.


## Chaining

When writing CSS rules, you may require an HTML element to have two or more CSS selectors at the same time. This is done by combining multiple selectors, which we refer to as *chaining*. 

for instance if we had multiple `<h1>` elements but one or more of them had had the `class` attribute with the `special` value, i.e.

``` <h1 class='special'> ```

Then, in CSS, we would write

``` h1.special { ... } ```

And this would *only* target the HTML elements of `<h1>` with the class "special". If a `<p>` paragraph element also had a class of "special" the rule would NOT apply.


## Descendant Combinator

This is how we target HTML elements that are nested inside of other HTML elements. Think the Parent / Child relationship of HTML code. Descendant Combinators are used to target the child, or "descendant", html.

If we have an ordered list `<ol class="main-list">` parent with list item `<li>` children, we can target the list items by writing in CSS:

``` .main-list li { ... } ```

Note that the `.` before main-list is necessary if we are targeting a class. If we were to be targeting a whole element nested inside of another element we could type:

``` li h4 { ... } ```

This would select any `<h4>` elements that were nested inside of a list item `<li>`


## Multiple Selectors

We can separate selectors with a comma if we want to target two or more separate elements and apply the same style to all of them

Instead of writing 

```
h1 {font-family:Georgia} 
.menu {font-family:Georgia}	
```

We could write 

``` h1, .menu {font-family:Georgia;} ```

____________________________________________________________________________________________________________________


# Visual Rules of CSS

There are some fundamental CSS VISUAL RULES that we need to be aware of.

## Font Family

Also known as the more technical term "typeface" is how we can specifiy what kind of font we want to use across the entire web page.

```h1 {font-family:Georgia;} ```

This would set any `<h1>` element to be rendered with the Georgia font. There are a few rules for declaring a font family:
	
- The Font being used must be installed on the user's computer or downloaded with the site
- WEB SAFE FONTS are a group of fonts that most browsers and operating systems already have
- Best to use web safe fonts so that your web pages are correctly displayed across as much PCs as possible
- If the font name is two or more words, put the font in quotes (single or double), i.e. {font-family:"Courier New";}

## Font Size 

The property `font-size` is pretty self explanatory; set the value to a number value followed by 'px', which stands for 'pixels'.
	
```h1 {font-size:18px;} ```

## Font Weight 

The property `font-weight` can be set to a few different values like `normal` or `bold` but can also be set to a numerical value starting at 1 and maxing at 1000, typically used in increments of 100.

```h1 {font-weight: bold;}```

## Text Alignment
	
The property `text-align` can be set to align text to either `left`, `center`, or `right`. A fourth option is also `justify` which spaces out text so that it aligns with bot the left and right side of the parent element. By default, all text aligns to the left side of whatever container it is in.
	
```h1 {text-align: center;}```

## Color and Background Color

These can be set by using the `color` and `background-color` properties and then assigning them a value. These values must be one of the following options:
	
- *Keywords* like blue, red, aquamarine, etc. 
- *RGB* (255, 150, 50) Where the number values are 0 - 255 which specify how much **red**, **green**, and **blue** are used.
	- *RGBA* (255, 150, 50, 0.5) can also be used, where 'A' represents 'alpha', which is a fancy word for opacity. A value of 1.0 would be fully opaque and a value of 0 would be transparent. If an alpha value is **not** specified the color will default to fully opaque (1.0).
- *HSL* (50, 100%, 50%) Where the first number represents the hue of a color wheel, ranging from 0-360. Then saturation and lightness, which are represented in a percentage value, where saturation represents how vibrant the color is (think color vs grayscale; 100% being full color) and lightness representing how much white vs black there is in the color value (100% being full white).
	- *HSLA* (50, 100%, 50%, 0.3) can also be used, and just like RGBA, the fourth number represents the alpha value.
- *Hex* Represented by 3-6 alpha-numeric characters like `#FFFFFF` or `#FFF`.
	
```h1 {color:red; background-color: (;}```

## Opacity
	
This can be set with the `opacity` property and can be set from a value of 0 to 1, where 1 is fully visibile and 0 is invisible.
	
```h1 {opacity:0.5;}```

## Background Image

This is used when we want to use an image as the background of an element instead of just a color. The value of the background-image property will be a url, which can either be an *internal* or an *external* link (i.e. somewhere in your project or somewhere on the internet). If it is internal it must be linked with a **relative file path**
	
External:

```.main-banner {background-image:url('https:www.url.com)}```
	
Internal:	

```.main-banner {background-image: url('images/mountains.jpg');```


## Important 

This can be applied to specific declarations instead of full rules. **It overrides ANY STYLE no matter how specific it is and as a result this feature should be used very sparingly.** However, sometimes we will need to use it, for example when we work with multiple stylesheets. The syntax is
	
```p {color:blue !important;}```

____________________________________________________________________________________________________________________

# The Box Model

Browsers load HTML elements with default positions and values and this can lead to unexpected user experiences and also limit the views you can create. For example, when you change the background color of an element sometimes there are unintended consequences, like the color stretching beyond the bounds of the element.
	
All elements are "living" inside of a box. This is the box we refer to in the *box model*. When you change the background color of an element you change the entire bg color of the box. These boxes have **dimensions**, **padding**, **borders**, and **margins**.

The *content* of the box is surroudned by the *padding*, which is surrounded by the *border*, and then surrounded by the *margin*.

## Height and Width
	
By default, these are set to hold the raw contents of the box. We can modify this by adding height and width properties in our CSS rules and then assigning them values.
	
```.class {height:300px; width: 600px;}```

## Borders
	
This is a line that surrounds an element, like a frame on a painting. Borders can have width, style, and color attributes.
	
- *Width* can be set by defining a pixel amount of using the values thin, medium, or thick.
- *Style* can be set to one of ten otions, none, dotted, and solid.
- *Color* can be set using hexcodes or built in keywords like red, blue, violet, etc.
- A borders default values are `medium, none, color` ; where color is the current color of the element. 
	
If width, style, or color are not given values in the CSS ruleset, then the default values will be used instead.

## Border Radius
	
This can be used to soften/round the corners of the box/border. For instance if we set the value of the border-radius to 5px then each corner will have a radius of 5px, as in the corners will match the curvature of a circle with a radius of 5px.

If we want to make a border that is a perfect cricle, we set the size of the box to be equal in height and weight, and then set the value of the border-radius to 50%.

```
{...
height: 60px; weight 60px; border: 2px solid red; border-radius: 50%;
...}
```

## Padding

This is the space between the *borders* of the box and the *content*. Padding is like the space between the frame and the picture. We can modify the space with the `padding` selector:
	
```{padding: 10px;}```
	
This would create a 10px padding on the top, right, bottom, and left.

### Padding Shorthand
- 4 Values 
	- We can also get more specific by using padding-top, padding-bottom, padding-left, padding-right properties and assigning them values OR we can write `{padding: 5px 6px 7px 8px;}`. This targets the padding in a clockwise direction, starting at the top. (5 top, 6 right, 7 bot, 8 left)

- 3 Values 
	- This can be used if we want to pad the left and right with the same value, but have different top and bottom values. The first value targets the top, second value targets left and right, and third targets with bottom.

- 2 Values 
	- This will pad the top and bottom with the first value and pad the left and right with the second.


## Margin

This is the space directly outside of the box and the rules can be modified exactly the same as padding and padding shorthand. We can also use the keyword `auto`, which lets you center the content. For example:

```
{...
width: 400px;
margin: 0 auto;
...}
```
	
This sets the top and bottom margin to 0px and then automatically adjusts the left and right so that the element stays centered within its containing element. In order to center and element we must set a width, otherwise it will be automatically set to the full width of its containing element, like <body> for example. Its impossible to center an element that takes up the full width of the page since the width can change due to display &/o browser window size. Setting the width to 400 in the previous code example will cause the div to center within a containing element that is greater than 400px wide.


## Margin Collapse

This refers to how overlapping vertical margin space works. **When there are two separate elements (boxes) next to each other (left and right) the margin space between the two boxes is sum of both elements margins.** So if `box-a` has a margin of 10px and `box-b` has a margin of 10px then the total horizontal space between them will be 20px.

**However, if there are two elements next to each other vertically (top/bottom) then the *total vertical space* between them will be whatever the largest margin value is.** For example if `box-a` is on top of `box-c`, and A has a bottom margin value of 10px and C has a top margin value of 30px, the vertical distance between the two elements would be 30px. This is **margin collapse*.

## Overflow
	
We can also set the min and max width of elements since web pages can be viewed thru displays of differing screen sizes. If the max height is set too low/small for the content, then the content will spill outside of the box.

The `overflow` property is how we control when content spills outside of its box. Some of the values we can assign this property include:
	
- `hidden` hides content that spills outside of the box
- `scroll` will add a scroll bar so that the rest of the content can be viewed by scrolling
- `visible` will allow the content to be visible outside of the box. **This is the default option.**

## Resetting Defaults

All major web browsers have default stylesheets the use in absence of an external one. These are known as *user agent stylesheets*, in this case the term "user agent" is a technical term for the browser.

Because of these user agent stylesheets, sometimes they interfere with your work as a web developer. Many devs choose to reset these default values so they can work with a clean slate, we do this by creating the CSS rule

```* {margin: 0; padding: 0;}```

This is often the first rule in an external stylesheet. Note that these values are set to 0 and not 0px, when these properties are set to 0 they do not require a unit of measurement.

## Visibility

The visibility of elements can be controlled with the `visiblity` property. We can set the value to hidden, visible, and collapse
- `hidden` Will hide the element
- `visible` Will make the element visible. **this is the default value**
- `collapse` Is only for table rows `<tr>`, row groups `<tbody>`, columns `<col>`, and column groups `<colgroup>`. This value removes a row or column, but it does not affect the table layout. The space taken up by the row or column will be available for other content. If `collapse` is used on other elements, it renders as "hidden"

**Note that even if the visiblity is set to hidden, users can still find it using inspect element and viewing the source code in their browser. Furthermore, the page will only hide the content, the space will still be reserved on the web page although it will be blank.**

____________________________________________________________________________________________________________________


# Changing the Box Model

The box model does have an awkward limitation regarding the box dimensions. If we have a box with a border of 1px, padding of 10px and a height & width of 200px by 300px, the height and width of the box are now 222px by 322px because of the 10px padding on either side and the 1px border as well. 

To prevent this from happening, we can control the box-sizing property of the CSS rule. By default its value is content-box; this is affected by the previously mentioned problem.

We can reset the entire box model and assign a new value: border-box

```* {box-sizing: border-box;}```

This will set all boxes to be of the border-box value. This keeps the height and width at a fixed value and the border thickness and padding values will be included inside of the box, meaning no overall dimensions of the box will change.

____________________________________________________________________________________________________________________


# Box Model in Dev Tools (Inspect Element)

Google Chrome has a thing called DevTools that web devs can use to see the box around every element of a web page. This can be incredibly useful for developers to figure out where content begins and ends.

On windows we can use CTRL+SHIFT+I to open the dev tools. Alternatively we can use F12 or also clicking the 3 vertical dot menu > more tools > developer tools

For example, open the DevTools, make sure elements is selected at the top, and in then click on Computed in the next section. This will show the element and when you hover over each part (content, padding, border, margin) it will be highlighted on the web page. If you know exactly what element you want to inspect, you can right click directly on the element in the webpage and click on Inspect Element and the DevTool will automatically take you to where that HTML code is located in the Inspect Element area.

You can also change the values by double clicking on the value in the Computed seciton and typing a new number. Note that this change is only temporary and does not override how everyone else experiences the webpage on their own browser. Also, if a borders property alue is set to - initially, and you change it to a number, the changes will not take effect as these values must be first set in the CSS rule sheet.


When using DevTools to check/proof read a web page, we can quickly create a border around all elements using DevTools. First select the HTML declaration in the elements pane <html...>, then in the styles pane, click on the plus icon to add a new rule, and add the rule 
	
```* {border:1px solid red;}```
	
Which will give every element a 1px red border that quickly helps you see the layout and content of a webpage.

____________________________________________________________________________________________________________________


# Flow of HTML
	
By default, the HTML elements of a webpage will render from left to right, top to bottom, in the same order that they exist in the document. This is called *flow*.

CSS not only controls how HTML elements are styled, but can also control where they are positioned. Properties such as `position`, `display`, `z-index`, `float`, and `clear` are some basic properties for adjusting positions of HTML elements in the browser.

## Position

This property controls the default position of an element. It can have the value of `static`, `relative`, `absolute`, `fixed`, or `sticky`. **The default value is static.**

`relative` places the element in a position that is *relative* to its default static position

If we declare the position value as relative, we still need to specify where the element should be positioned on the page. We do this by accompanying the position declaration with one or more of the *offset properties*, top, bottom, left, &/o right.
	
- `Top` moves the element down from the top
- `Bottom` moves the element up from the bottom
- `Left` moves the element away from the left side (towards the right)
- `Right` mvoes the element away from the right side (towards the left)
	
These values can be set as `pixels`, `ems`, or `percentages`, among others. **These offset properties will not work if the value of the position property is static.**

`absolute` makes it so that all other elements on the page will ignore the element with the absolute position value and act as if it is not present on the page. The element will be positioned relative to its closest positioned parent element, while offset properties can be used to determine the final position from there. When an element is set to absolute, the element will scroll with the rest of the document when the user scrolls.

`fixed` will fix the element to a specific position on the page regardless of user scrolling. Set the value to fixed and accompany it with offset properties. For example, if we give the <nav> box a fixed position property, then it will stay at the top of the screen even when the user scrolls down/up.

**Static and Relative keeps the element flowing with the rest of the document, while Absolute and Fixed prevent the element from flowing with the document.**

`sticky` keeps an element flowing as the user scrolls but will STICK to a specified position as the page scrolls further.

```{...position:sticky; top: 240px;}```

Will keep the position at 240px from the top until it reaches the its correct place in the parent element and then will "unstick"


## Z-Index

This is how we order things from front to back. When elements overlap each other it can be difficult to read/consume, so we use `z-index` to determine which elements have priorty (i.e. when overlapped, which elements will appear "on top/in front" and which elements will appear "on bottom/behind" each other). The value is set with an integer and by default all elements have a value of 0. 
	
**If one element has a z-index of 1, and the other has a z-index of 0, the element with the value of 1 will appear in front of the other element.**


## Inline Display

Inline elements such as `<em>`, `<strong>` and `<a>` only take up as much space necessary to display their conent. The height and width cannot be specified in the CSS document. Inline elements have a box that wraps tightly around the content.

By using the `inline` property on elements that are not inherently inline, we can apply the same style/effect to them.

h1 {display: inline;}

The browser will render `<h1>` elements on the same line as other inline elements immediately before or after them (if there are any).


## Block-Level Elements

These elements are not displayed on the same line as the content around them. These elements fill the entire width of a page by default, but their width property can also be set. Unless otherwise specified, the height will automatically be set to whatever height is needed to fit the content.

Elements like heading elements `<h1> - <h6>`, `<p>`, `<div>`, and `<footer>` are all block level elements.

## Inline-Block

These elements combine feature of inline and block elements. THey can appear next to each other and we can specify their dimensions using the width & height properties. Images are the best example of default inline-block elements. If we have three separate `<div class="rectangle"> ... </div>` elements, by default they would render vertically. However if we use the CSS styling:

```.rectangle {display: inline-block; width 200px; height 300px;}```

The boxes will be rendered inline (next to each other horizontally) with the set height and width values.

- `inline` elements appear next to each other/on the same line but CANNOT have their height and width properties set. 
- `block` elements are not displayed on the same line and CAN have their width and height properties set. 
- `inline-block` elements have their height and width properties set AND appear on the same line as the other elements, provided they have enough space


## Float

The `float` property can be used to move the element as far left or as far right as possible in the container. As opposed to giving it an exact position using offset properties. `float` is commonly used for wrapping text around an image, note however that moving elements left or right for layout purposes is better suited for tools like CSS gridbox and flexbox.

The `float` property is often set either using the value of `left` or `right`. This works for static or relative positioned elements. **Floated elements MUST HAVE A WIDTH specified**, otherwise the element will assume the full width of its containg element and changing the float value will not yield any visible results.

`float` can be used to affect multiple elements at once, however when multiple elements are floated and thye have different heights it can affect the layout of the page. Specifically, elements can "bump" into each other and not allow other elements to properly move left or right.

## Clear

This property specifies how elements should behave when they bump into each other on the page. The value can be left, right, both, or none.
- `left` prevents the left side of the element from touching any other element within the same containing element.
- `right` prevents the right side of the element from touching
- `both` prevents left and right side from touching other lemeents
- `none` the element CAN touch either side

____________________________________________________________________________________________________________________


# Colors
	
These can be definied using keywords, RGB, or HSL, and also HEX color codes. We can change both the color (foreground) and background-color of an element.

## Keywords 
	
We can use keyword values like "red", "blue", "violet" to define the `color` property value.
	
```p {color: green};```

## RGB and HSL
	
These use 3 values to represent the Red Green and Blue or Hue Saturation and Lightness. 

```p {color: rgb (23, 45, 23);```
	
- These numbers must be between 0 and 255.
	
```p {color: hsl (255, 150, 100};```
	
- The first number HUE must be set between 0 and 360 which represents the angle on a color wheel.
- The second number SATURATION must be between 0 and 100% and represents how intense/rich/vibrant the color is.
- The last number is LIGHTNESS and must be between 0 and 50%. 50% is "normal", 0 is dark(black) and 100 is light(white).

## HEX 
	
These are color codes that use a # symbol and a combination of 6 letters &/o numbers
	
```p {color: #FFFFFF};```
	
- If a hex color code has triple repeating double characters, for example #BB44FF, it can be shortened down to #B4F.

## Opacity and Alpha

Colors can also have an opacity or alpha value. We can do this by using rgba or hsla instead of rgb or hsl. This means we also have to include a fourth value in the declaration which must be between 0 and 1.

We can also add alpha values to hex color codes. If using a 6 digit hex code, add 2 extra digits at the end representing the percentage of opacity. These additional hex digits can range from 00 (transparent) to FF(opaque). Think about how alpha masks in photoshop work. Everything that is in black is masked out and everything that is in white is still visible. Therefore, when the hex alpha is 00, the value is "black" and the visibility is "0/fasle". When the hex alpha is FF, the value is "white" and the visiblity is "1/true".

Alpha values cannot be applied to named colors, only RGB, HSL, or HEX color codes. However there is a named color keyword for 0 opacity, and that is "transparent" which is equivalent to rgba (0,0,0,0), and can be written like:
	
```p {color:transparent;}```

____________________________________________________________________________________________________________________


# Typography

We can set the `font-family` property by typing
	
```h1 {font-family: arial;}```

However, if the name of the font is multiple words, the font name must be encapsulated by quotes.
	
```h1 {font-family: 'Times New Roman';}```

## Web Safe Fonts
	
This refers to the group of fonts that are widely used by major web browsers and are safe to use on web pages without having to worry about wether or not the font will show. If the webpage uses a *non-web safe font*, the font must be installed on the device that is viewing the web page.


## Fallback Fonts & Font Stacks

These can be used as a way to create contingency plans for if certain text don't work.
	
```h1 {font-family: Caslon, Georgia, 'Times New Roman';}```

This is whats called a **font stack**. The browser will first try to use Caslon, and if unable to do that will use Georgia, and then if unable to use that will use Times New Roman. It usually contains a list of similar-looking fonts. Each subsequent font after the first (Caslon) is a **fallback font**.

## Serif and Sans-Serif
	
This refers to two different styles of typefaces. **Serif** refers to the little tail things like you see on Times New Roman, and **Sans-Serif** refers to fonts that do not have it, like Arial. Serif fonts are typically used in print, like newspapers, while Sans Serif is typically used for digital media. 

`serif` and `sans-serif` are also keyword values that can be added as the final fallback font if nothing else in front of the stack are available.

```h1 {font-family: Caslon, Georgia, 'Times New Roman'; serif;}```

In the above example, if any of the first 3 fonts arent available, the browser will use whatever serif font is available on the system.

## Font Weight

The `font-weight` property can be specified with either keywords of numerical values. Keywords are BOLD, NORMAL (default value), LIGHTER (one font weight lighter than elements parent value), or BOLDER (one font weight bolder than element's parent).

Numerical values can always be used from 1 to 1000, with 1 being the lightest and 1000 boldest. A weight of 400 is equal to normal, 700 is equal to bold. Its best practice to use increments of 100. Its important to knwo that not all fonts can be assigned numeric font weight, and not all numeric font weights are available to all fonts. Its best to look up the font and see what avaialbe font weight values are available.

## Font Style

The `font-style` property is a way to italicize text. By default the font-style is of a normal value.

```h1 {font-style: italic;}```

## Text Transformation

The `text-transform` property is a way to make the text either all uppercase or all lowercase.
	
```h1 {text-transform: uppercase;}```

## Letter Spacing
	
The property `letter-spacing` is used to set the horizontal spacing between the individual characters in an element. Its not common to have to do this but sometimes it can be useful. This property cna take length values in units, such as 2px or 0.5em.
	
```p {letter-spacing: 2px;}```

## Word Spacing

`word-spacing` works in a similar way and sets the horizontal spacing between each word. It takes values as units such as 3px or 0.5em;

```h1 {word-spacing: 2px;}```

## Line Height

The `line-height` property can be specificed to set how tall we want each line containing our text to be. Line height can be a unitless number, such as 1.2 or a unit value such as 12px, 5%, or 2em. Typically, a unitless number such as 1.2 is preferable, because it is responsive based on current font size. In other words, if the line height value is 1.2, it will automatically adjust if the font size is changed.
	
```p {line-height: 14.}```

## Text Alignment
	
The `text-align` property is used to align text to its parent element.

```p {text-align: justify;}```

## Web Fonts

Web Fonts are different than web safe fonts. Web fonts allow you to to <link> a font from something like Google Fonts or Adobe Fonts, in your HTML documents. You can also used paid fonts from font distributors like fonts.com by downloading them and hosting them with the rest of your site's files. You can create a @font-face ruleset in your CSS stylesheet to link to the relative path of the font file.

Both techniques allow you to go beyond the sometimes "traditional" apperance of web safe fonts.

For Example, if we use Google Fonts, after we find the font that we want to use, a <link> element will be automatically generated. We can then add that element to our <head> element of HTML, and then use that font in our CSS styling.

Fonts can also be added using the @font-face ruleset in your CSS stylesheet, isntead of the <link> element in your HTML document. Downloaded fonts come in a few file formats such as OTF(OpenType Font), TTF (TrueType Font), WOFF(Web Open Font Format) WOFF2(Web Open Font Format 2). The different formats are a progression of standards for how fonts will work with different browsers, with WOFF2 being the most progressive. Its a good idea to unclude TTF, WOFF, and WOFF2 with your @font-face rule to ensure compatibility on all browswers.

When you download the font files to your computer, its a good idea to make sure you generate additional file types for the same font. For example, if we are downloading the Roboto font, by default it will be a .TFF file. We should also generate a .WOFF and .WOFF2 version of the ROBOTO font as well.

When you have all the files you need, move them to a folder inside your website's working directory and you're ready to use them in a @font-face ruleset, for example:

```
@font-face {
	font-family: "MyParagraphFont";
	src: url('fonts/Roboto.woff2') format('woff2'),
	src: url('fonts/Roboto.woff') format('woff'),
	src: url('fonts/Roboto.ttf') format('truetype'),
}
```

It's recommended to define the @font-face ruleset at the top of your CSS stylesheet. When you use a downloaded font you can set the name of the font to a custom name, in the above exmaple it is "myparagraphfont". The src property contains 3 values, each specifiying the relative path to the font file and its format. The order of the different formats is important because our browswer will start at the top of the list and search until it finds a font format it supports. Once the @font-face rule is defined, you can use your custom named font on your style sheet, for example:

```p {font-family: "myparagraphfont", sans-serif;}```

____________________________________________________________________________________________________________________

# Flexbox

Previously, we learned about the box model of CSS display and the many tools and properties we can manipulate to position elements on a webpage. Flexible Box Layout, or *Flexbox*, is a tool that greatly simplifies how to position elements.

There are two important components to a flexbox layout: *flex containers* and *flex items*.

## Flex Containers 

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

In the example above, all divs with the class container are flex containers. If they have children, the children are flex items. A div with the declaration `display: flex;` will remain block level and no other elements will appear on the same line as it. However, it will change the behavior of its child elements. Child elements will not begin on new lines.

## inline-flex

When we give a div - a block level element - the `display: flex` property, it remains a block level element. But what if we want multiple flex containers to display inline with each other? 

If we **did not** want div elements to be block-level elements, we would use `display: inline;` However, flexbox provides the `inline-flex` value for the `display` property which allows us to create flex containers that are also inline elements.

```
<div class='container'>
  <p>I'm inside of a flex container!</p>
  <p>A flex container's children are flex items!</p>
</div>
<div class='container'>
  <p>I'm also a flex item!</p>
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
In the example above, the .child divs will take up more width (300 pixels) than the container div allows (200 pixels). The .child divs will shrink to accommodate the container's size.

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

- `flex-start` : all items to be positioned in order starting from the left of the parent container with no extra space between or before them
- `flex-end` : all items will be positioned in order, with the last item starting on the right side of the parent container with no extra space between or before them.
- `center` : all items will be positioned in order, in the center of the parent container, with no extra space before, between, or after them.
- `space-around` : items will be positioned with equal space before and after each item, resulting in double the space between elements
- `space-between` : items will be positioned with equal space between them, but no extra space ebfore the first or after the last elements.

"No extra space" meaning that margins and borders will be respected, but no more space (than what is specified in the style rules for the particular element) will be added between elements. The size of each individual flex item is not changed by this property.

## align-items

It is possible to align flex items vertically within the container with the `align-items` property.

```
.container {
  align-items: baseline;
}
```
In the example above, the align-items property is set to baseline. This means that the baseline of the content of each item will be aligned. Below are some common values used for the `align-items` property:

- `flex-start` : all elements will be positioned at the top of the parent container.
- `flex-end` : all elements will be positioned at the bottom of the parent container.
- `center` : the center of all elements will be positioned halfway between the top and bottom of the parent container.
- `baseline` : the bottom of the content of all items will be aligned with each other.
- `stretch` : if possible, the items will stretch from top to bottom of the container (this is the default value; elements with a specified height will not stretch; elements with a minimum height or no height specified will stretch).

These values tell the elements how to behave along the *cross axis* of the parent container, which stretches from top to bottom.

You might be unfamiliar with the `min-height` and `max-height` properties, but you have used `height` and `width` before. `min-height`, `max-height`, `min-width`, and `max-width` are properties that ensure an element is at least a certain size or at most a certain size, but we will cover that a bit further ahead.

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

**Note that the `flex` *property* is different than the `flex` *value* used for the `display` property**

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

**Note that there *is no way* to set shrink and basis using 2 values.**

## flex-wrap

Sometimes, we don't want our content to shrink to fit its container. Instead, we might want flex items to move to the next line when necessary. This can be declared with the `flex-wrap` property. The `flex-wrap` property can accept three values:

- `wrap` child elements of a flex container that don't fit into a row will move down to the next line
- `wrap-reverse` has the same functionality as `wrap`, but the order of rows within a flex container is reversed (for example, in a 2-row flexbox, the first row from a `wrap` container will become the second in `wrap-reverse` and the second row from the wrap container will become the first in `wrap-reverse`)
- `nowrap` prevents items from wrapping; this is the default value and is only necessary to override a wrap value set by a different CSS rule.

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

- `flex-start` : all rows of elements will be positioned at the top of the parent container with no extra space between.
- `flex-end` : all rows of elements will be positioned at the bottom of the parent container with no extra space between.
- `center` : all rows of elements will be positioned at the center of the parent element with no extra space between.
- `space-between` : all rows of elements will be spaced evenly from the top to the bottom of the container with no space above the first or below the last.
- `space-around` : all rows of elements will be spaced evenly from the top to the bottom of the container with the same amount of space at the top and bottom and between each element.
- `stretch` : if a minimum height or no height is specified, the rows of elements will stretch to fill the parent container from top to bottom (default value).

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

- `row` : elements will be positioned from left to right across the parent element starting from the top left corner (default).

- `row-reverse` : elements will be positioned from right to left across the parent element starting from the top right corner.

- `column` : elements will be positioned from top to bottom of the parent element starting from the top left corner.

- `column-reverse` : elements will be positioned from the bottom to the top of the parent element starting from the bottom left corner.

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
13. Flex containers can be nested inside of each other by declaring `display: flex` or `display: inline-flex` for children of flex containers.

____________________________________________________________________________________________________________________
	
# Basic CSS Grid

CSS has many tools to elegantly lay out elements of a web page. There is no simple answer or no correct way to do this, it all depends on the content you are trying to display, and just like anything in programming there are always multiple different techniques to solve a problem.

We've learned about the box model, display/positioning, and flexboxes so far. This section is about *CSS Grid*. 

Whereas flexbox is mostly useful for positioning items in a one-dimensional layout, CSS Grid is most useful for two-dimensional layouts, providing many tools for aligning and moving elements across both rows and columns.

## Creating a Grid

To set up a grid we need both a *grid container* and *grid items*. The grid container is the parent element that contains the grid items as its child elements and applies overarching styling and positioning to them.

To turn an HTML element into a grid container, you must set the element's `display` property to one of two values:

- `grid` which makes block-level grid
- `inline-grid` which makes an inline grid

From there we can assign other proeprties to lay out the grid to suit our needs.

## Creating Columns

By default, grids only contain one column. When you add new items into the grid container, each new item appears on a new row. To change this we need to explicitly define the number of rows and columns in the grid.

We can do this by using the property `grid-template-columns`.

```
.grid {
  display: grid;
  width: 500px;
  grid-template-columns: 100px 200px;
}
```
This creates two columns in the grid, the first one being 100px wide and the second being 200px. For every value added, there will be another corresponding column. So if there were 5 values, 100px 200px 200px 200px 100px, there would be 5 columns.

We can also define these values as percents instead of pixels.

```.grid {
display: grid;
width: 1000px;
grid-template-columns: 20% 50% 10%}
```

Since the width of the grid is 1000px, the first column would be 20% of 1000px, or 200px. The second would be 500px, and the third column would be 100px.

We can also mix and match these values

```.grid {grid-template-columns: 100px, 20%, 500px}```

However, we should be careful to not set these values to exceed the width of the grid, this results in overflow which we will discuss further into this section.

## Creating Rows

This property is almost identical to `grid-template-columns` and takes values in a similar manner.

```
.grid {
height: 500px;
grid-template-rows: 10% 20% 600px;}
```

This would create three rows, the first being 50 pixels tall  (10% of 500px), the second being 100pixels tall (20% of 500px), and the third being 600px tall.

Remember that when using percentages in these two properties, rows are a percentage of the grid's height while columns are a percentage of the grid's width.

## Grid Template

We can use the `grid-template` property as a shorthand for both `grid-template-columns` and `grid-template-rows`.

```
.grid {grid-template: 200px 300px / 20% 10% 70%;}
```
The first values beofre the slash specify the row sizes and the values after the slash represent the columns. The same rule about percentages applies with this property as well.

## Fraction

We can use the `fr` unit of measurement, as opposed to `px`, `em`, `%` as a way to specify *fractions* of the grid. This can be used both in rows and columns and was specifically created for use in the CSS Grid. Using `fr` helps to prevent grid items from overflowing.

```
.grid {grid-template: 2fr 1fr 1fr / 1fr 3fr 1fr;}
```
This grid would have three rows and three columns. The rows would split whatever the designated `height` property was into four parts (2+1+1) and give the first row 2/4 of the space and the remaining two rows would get 1/4 each. The columns would split whatever the designated `width` property was into five parts (1+3+1) and then split the columns into 1/5, 3/5, and 1/5 respectively.

It is also possible to mix and match `fr` with other units of measurement and when we do this each `fr` represents a fraction of the remaining available space. For example:

```
.grid {
  display: grid;
  width: 100px;
  grid-template-columns: 1fr 60px 1fr;
}
```
Here, the second column is designated to take up 60px, leaving 40px remaining. Each `1fr` value would be 1/2 the remaining 40px, which would be 20px each.

## repeating()

The previous properties can also take a function as a value. We can use `repeat()` as one of those functions which was also created specifically for CSS Grid.

```.grid {grid-template-columns: repeat (3, 100px);}```

This would create three columns of 100px wide each. `repeat()` is particularly useful with `fr` in creating equal size rows or columns. We can also use multiple values in the `repeat()` function

```grid-template-columns: repeat(2, 20px 50px)```

This would create four columns where the first and third would be 20px wide and the second and fourth would be 50px wide.

## minmax()

So far we have only covered grids with a fixed size but sometimes you might want a grid to resize based on the size of the web browser.

In these situations, you may want to prevent a row or colum from being too big or too small. For example, if you have a 100px wide image in your grid you probably don't want its column to be smaller than 100px wide. This is where `minmax()` comes in handy.

```
.grid {
  display: grid;
  grid-template-columns: 100px minmax(100px, 500px) 100px;
}
```
In this example we have three columns, the first and third colum are 100pixels but the second column will vary in size. The `minmax()` function will cause the second column to be no smaller than 100px and no larger than 500px.


## Grid Gap

We can use the `column-gap`, `row-gap`, and `gap` properties to provide blank space between our grid items. It is important to remember that these properties will not add a gap at the beginning or the end of the grid.

The `gap` property is a shorthand way of including the `row-gap` and the `column-gap` into one property.

```gap: 20px 10px;```

When using 2 values the first is the row gap and the second is the column and if we use 1 value then that is the gap for both rows and columns.

## Grid Item

So far we have learned how to define a grid container and each grid item has only taken up exactly one square of the grid. Most of the time, that's not how we want to design our websites as it is boring and can be too symmetrical. In the following sections we will learn how to make grid items span multiple rows &/o columns to create interesting designs and layouts.

## Multiple Row Items

Using the properties `grid-row-start` and `grid-row-end` we can make a single grid item span multiple rows. Remember that we are no longer applying CSS styling to the outer grid container, we are now styling the grid item inside of the grid container.

```
.item {
  grid-row-start: 1;
  grid-row-end: 3;
}
```
n this example, the HTML element of class item will take up two rows in the grid, rows 1 and 2. Notice that the `grid-row-end` value is 3 but it only spans rows 1 and 2. Row grid lines and column grid lines start at 1 and end at a value that is 1 greater than the number of rows or columns the grid has. For example, if a grid has 5 rows, the grid row lines range from 1 to 6. If a grid has 8 rows, the grid row lines range from 1 to 9.

The value for `grid-row-start` should be the row at which you want the grid item to begin. The value for `grid-row-end` should be one greater than the row at which you want the grid item to end.

It is also possible for the start value to be greater than that of the end value and both properties can also each have negative values.

## Grid Row

We can use `grid-row` as a shorthand for both `grid-row-start` and `grid-row-end`.

```
.item_a {
  grid-row-start: 4;
  grid-row-end: 6;
}

.item_b {
  grid-row: 4 / 6;
}
```

Both of these rulesets would yield the same results. The number before the slash is the row start and the number after the slash is the row end.

When an item spans multiple rows or colums using these properties it will also include any `gap` that exists. For example, if an item spans two rows of `height` 100px and there is a 10px `gap`, then the item will have a total height of 210px.

## Grid Column

`grid-column-start`, `grid-column-end`, and `grid-column` work identically to the row properties we just covered. These properties allow a grid item to span multiple columns.

When using these properties (`grid-row-etc` and `grid-column-etc`) we can also use the keyword `span` to start or end a column or row relative to its other end.

```
.item_a {
  grid-column: 4 / span 2;
}

.item_b {
  grid-column: 4 / 6;
}
```
Both of these rulesets would yield the same result. The keyword `span` can be incredibly useful because it helps us avoid the "off-by-one" errors you might make when determining the ending grid line of an element.

## Grid Area

We can also use the `grid-area` property as a shorthand for `grid-column-start`, `grid-column-end`, `grid-row-start`, and `grid-row-end`. This property takes four values which are all separated by slashes and the order of these values are incredbily important!

```
.item {
  grid-area: 2 / 3 / 4 / span 5;
}
```

The first value is the row start, the second value is the column start, the third value is the row end, and the fourth value is the column end.
____________________________________________________________________________________________________________________
	
# Advanced CSS Grid	
	
## Grid Template Areas

The `grid-template-areas` property allows you to name sections of your web page that you can use as values in the `grid-row-start`, `grid-row-end`, `grid-column-start`, `grid-column-end`, and `grid-area` properties. 

**This property is declared on grid containers**

```
grid-template-areas: "head head"
                       "nav nav" 
                       "info services"
                       "footer footer";
```

- This tells us that the area name "head" will take the space of row 1, column 1 and row 1, column 2
- The area named "nav" will do the same and take the space of row 2, column 1 and row 1, column 2.
- This next part tells us that "info" will take up row 3, column 1 and "services" will take up row 2, column 2.
- This part tells us "footer" will take up the space of row 4, column 1 and row 4, coulmn 2.

## Overlapping Elements

Another powerful feature of CSS Grid Layout is the ability to easily overlap elements. When we overlap elements, it is generally easiest to use the `grid-area` property with grid row names. 

```
.container {
  display: grid;
  grid-template: repeat(8, 200px) / repeat(6, 100px);
}
 
.info {
  grid-area: 1 / 1 / 9 / 4;
}
 
.services {
  grid-area: 1 / 4 / 9 / 7;
}
 
img {
  grid-area: 2 / 3 / 5 / 5;
  z-index: 5;
}
```
We can see in the following code that the `img` will overlap (i.e. exist in the same rows & columns) both the `.info` and `.services` elements of our web page. 

By using the `z-index` property we can designate that it will render in front of both the `.info` and `.services` elements.

## Justify Items

We have mentioned "two-dimensional grid-based layouts" a few times. This means that there are 2 axes in our grid layout, the horizontal/row axis and vertical/column axis otherwise known as the block axis and the inline axis.

The `justify-items` property allows us to position grid items along the inline, or row, axis. This means that it positions items from left to right across the web page.

**This property is declared on grid containers** and accepts values such as:

- `start` which aligns grid items to the left side of the grid area
- `end` which aligns grid items to the right side of the grid area
- `center` which aligns grid items to the center of the grid area
- `stretch` which stretches all items to fill the grid area

There are several other values that can be used for the `justify-items` property that you can find more information about in the [documentation](https://developer.mozilla.org/en-US/docs/Web/CSS/justify-items#Values).It is important to note that the page with the definitions includes some values that are not accepted in CSS Grid layout.

## Justify Content

If `justify-items` is how we position *grid items* within their columns along the inline axis, then we can use `justify-content` to position *the entire grid* along the inline axis.

**This property is declared on grid containers** and accepts these values:

- `start` aligns the grid to the left side of the grid container
- `end` aligns the grid to the right side of the grid container
- `center` centers the grid horizontally in the grid container
- `stretch` stretches the grid items to increase the size of the grid to expand horizontally across the container
- `space-around` includes an equal amount of space on each side of the grid element. There will be half as much spafe before the first element and after the last element as there is between elements.
- `space-between` includes an equal amount of space between grid items with no space at either end
- `space-evenly` places an even amount of space between grid items and either ends

Just as before, there are other values we can use for this property which can be found in the [documentation](https://developer.mozilla.org/en-US/docs/Web/CSS/justify-content#Values) however some of these values will not be accepted in CSS Grid Layout.

## Align Items

We can use the `align-items` property to position grid items along the horizontal, or block, axis. **This property is declared on grid containers** and accepts these values:

- `start`
- `end`
- `center`
- `stretch`

Consult the [documentation](https://developer.mozilla.org/en-US/docs/Web/CSS/justify-items#Values) for other accepted values and remember that not all values in the documentation will be accepted in CSS Grid Layout.

## Align Content

Just like we learned the difference between `justify-content` and `justify-items`, the same goes for `align-items` and `align-content`. The `align-content` property positions the rows along the horizontal axis and is **declared on grid containers**. It accepts the values

- `start`
- `end`
- `center`
- `stretch`
- `space-around`
- `space-between`
- `space-evenly`

Here is the [documentation](https://developer.mozilla.org/en-US/docs/Web/CSS/align-content#Values) and remember not all values are accepted in CSS Grid Layout.

## Justify Self and Align Self

`justify-items` and `align-items` specify how *all grid items* in a container will position themselves. The `justify-self` and `align-self` properties control how *individual grid items* will position themselves.These properties override the `justify-items` and `align-items` properties.  **These properties are declared on the grid items themselves NOT the grid container** and accept these values:

- `start`
- `end`
- `center`
- `stretch` 

## Implicit vs. Explicit Grid

So far, we have been *explicitly* defining the dimensions and quantities of our grid elements. This works well in many cases like a landing page for a business that will always display specific information at all times.

However, there are instances when we don't know how much information is going to be displayed. For example, consider online shopping; Often these web pages include an option to display x-amount of items per page but then also offer the ability to can display *all* items on a single page. When displaying all items on one page, the web developer cannot know in advance how many elements will be in the search results.

What about if the developer has specified a 3-column, 5-row grid (total 15 items) but the search results return 30?

This is where *implicit* grids take over; This determines the default behavior for the placement of elements when there are more than will fit into the grid specified by the CSS.

By default, the implic grid works as follows: Items will fill up exisitng rows first and then add new rows as necessary. New grid rows will only be tall enough to contain the content within them.

## Grid Auto Rows and Grid Auto Columns

CSS Grid provides two properties to specify the size of grid tracks added implicitly: `grid-auto-rows` and `grid-auto-columns`. **These properties are declared on grid containers**.

`grid-auto-rows` specifies the *height* of implicitly added grid rows and `grid-auto-columns` specify the *width* of implicitly added grid columns. They accept the same values as their grid-template counterparts:

- `px` pixels
- `%` percentages
- `fr` fractions
- `repeat()` repeat function

If we do not specify `grid-auto-rows` in our ruleset(s) the rows would be auto adjusted to the height of the content of the grid items.

## Grid Auto Flow

In addition to setting the dimensions for implicilty-added rows and columns, we can also specify the order in which they are rendered.

`grid auto flow` deisgnates whether new elements should be added to rows or columns. **This property is declared on grid containers** and accepts these values:

- `row` new elements will fill rows from left to right and create new rows when there are too many elements in a given row
- `column` new elements should fill columns from top to bottom and create new columns where there are too many elements in a given column
- `dense` this keyword invokes an algorithm that attempts to fill holes earlier in the grid layout if smaller elements are added.

We can also pair these values like this: `grid-auto-flow: row dense`.

## Summary

- `grid` template-areas specifies grid named grid areas
- grid layouts are two-dimensional: they have a row, or inline, axis and a column, or block, axis.
- `justify-items` specifies how individual elements should spread across the row axis
- `justify-content` specifies how groups of elements should spread across the row axis
- `justify-self` specifies how a single element should position itself with respect to the row axis
- `align-items` specifies how individual elements should spread across the column axis
- `align-content` specifies how groups of elements should spread across the column axis
- `align-self` specifies how a single element should position itself with respect to the column axis
- `grid-auto-rows` specifies the height of rows added implicitly to the grid
- `grid-auto-columns` specifies the width of columns added implicitly to the grid
- `grid-auto-flow` specifies in which direction implicit elements should be created
	
____________________________________________________________________________________________________________________

# Sizing Elements - Responsive Design

## Relative Measurements

We can view webpages with many different devices: phones, desktop monitors, tablets, etc. and every device has different screen sizes. As web developers, how do we ensure that the content on a webpage can be viewed in a readable and visually appealing way across all devices, regardless of screen size?

*Responsive design* refers to the ability of a website to resize and reorganize its content based on:

1. The size of the other content on the website
2. The size of the screen the website is being viewed on

When we size content with `pixels` we are giving the element *exact* dimensions, meaning that it will always be the designated size. If the screen size were to change, like switching from landscape to portrait mode on a phone, elements with a fixed size may appear too small, overflow the screen, or become completel illegible.

We can avoid hard coded exact measurements and use *relative measurements* instead to solve these problems. This allows content to remain in proportion regardless of screen size and layout.

## Em

One unit of measurement we can use instead of `pixels` is `em`. 

`em` represents the font size of the current element or the default base font size set by a browswer if none is given. For example, if the base font of a browser is 16px, then `1em` is equal to 16px. `2m` would be equal to 32px, and so on. 

## Rem

`rem` stands for *root em* and acts similar to em but instead of checking the *parent element's* font size, it checks the *root element*. The root element is the `<html>` tag.

Most browswers set the font size of the `<html>` to 16px, so by default rem measurements will be comapred to that value. If we want to set the root element font size to a different value, we need to create a ruleset in our css stylesheet.

```
html {font-size: 20px}
```

Now, if we set any future font-size to something like `2rem` or `5rem` the elements would be 40px and 100px, respectively.

One advantage of using rems is that all elements are compared to the same font size value, making it easy to predict how large or small font will appear. If you are interested in sizing elements consistently across an entire website, the rem measurement is the best unit for the job. If you’re interested in sizing elements in comparison to other elements nearby, then the em unit would be better suited for the job.

## Percentages: Height & Width

To size non-text HTML elements relative to their parent elements on the page we can use *percentages*.

Percentages are often used to size box-model values, like width, height, padding, border, and margins. They can also be used to set position properties (top, bottom, left, right).

```
.main {
  height: 300px;
  width: 500px;
}
 
.main .subsection {
  height: 50%;
  width: 50%;
}
```
When percentages are used, elements are sized relative to the dimensions of their parent element, (read: container). Therefore, the dimensions of the `.subsection` div above will be 150px tall and 250px wide. Be careful, a child element’s dimensions may be set erroneously if the dimensions of its parent element aren’t set first.

Because the box model includes padding, borders, and margins, setting an element’s `width` to `100%` may cause content to overflow its parent container. While tempting, `100%` should only be used when content will not have padding, border, or margin.

## Percentages: Padding and Margin

Percentages can also be used to set the padding and margin of elements.

When height and width are set using percentages, you learned that the dimensions of child elements are calculated based on the dimensions of the parent element.

When percentages are used to set padding and margin, however, they are calculated based only on the *width* of the parent element.

Vertical padding and margin are also calculated based on the width of the parent. Why? Consider the following scenario:

1. A container div is defined, but its height is not set (meaning it’s flat).

2. The container then has a child element added within. The child element does have a set height. This causes the height of its parent container to stretch to that height.

3. The child element requires a change, and its height is modified. This causes the parent container’s height to also stretch to the new height. This cycle occurs endlessly whenever the child element’s height is changed!

In the scenario above, an unset height (the parent’s) results in a constantly changing height due to changes to the child element. This is why vertical padding and margin are based on the width of the parent, and not the height.

Note: When using relative sizing, ems and rems should be used to size text and dimensions on the page related to text size (i.e. padding around text). This creates a consistent layout based on text size. Otherwise, percentages should be used.

## Width: Minimum & Maximum

Sometimes elements can lose their integrity when they become too small or too large. We can use the `min-width` and `max-width` properties to circumvent this problem.

We can use pixel values with these properties to ensure hard limits on the dimensions of the elements.

## Height: Minimum & Maximum

Similarly to the above section, we can also set the `min-height` and `max-height` properties as well.

If we set the `max-height` property too low for an element, its possible that the content will overflow outside of the element resulting in illegible content.

## Scaling Images and Videos

Websites often contain media, like images and videos, and its important to make sure that these are scaled proportionally so that users can view it correctly.

```
.container {
  width: 50%;
  height: 200px;
  overflow: hidden;
}
 
.container img {
  max-width: 100%;
  height: auto;
  display: block;
}
```
In this example, the `.container` represents a container div. Setting the `overflow` property to `hidden` ensures that any content with dimensions larger than the container will be hidden from view.

The second ruleset ensures that images scale with the width of the container. The `height` property is set to `auto`, meaning that an image's height will *automatically* scale proportionally with the width.

**It’s worth memorizing the entire example above. It represents a very common design pattern used to scale images and videos proportionally.**

The example above scales the width of an image (or video) to the width of a container. If the image is larger than the container, the vertical portion of the image will overflow and will not display. To swap this behavior, you can set `max-height` to `100%` and `width` to `auto` (essentially swapping the values). This will scale the *height* of the image with the height of the container instead. If the image is larger than the container, the horizontal portion of the image will overflow and not display.

## Scaling Background Images

We can also responsively scale background images of HTML elements.

```
body {
  background-image: url('#');
  background-repeat: no-repeat;
  background-position: center;
  background-size: cover;
}
```
In the example above, the image will *cover* the entire background of the element while keeping the image in proportion. If the dimensions of the image exceed the dimensions of the container, then only a portion of the image will display.

## Summary

- Content on a website can be sized relative to other elements on the page using *relative measurements*.
- The unit of `em` sizes font relative to the font size of a parent element.
- The unit of `rem` sizes font relative to the font size of a root element. That root element is the `<html>` element.
- Percentages are commonly used to size box-model features, like the width, height, padding, or margin of an element.
When percentages are used to size width and height, child elements will be sized relative to the dimensions of their parent (remember that parent dimensions must first be set).
- Percentages can be used to set padding and margin. Horizontal and vertical padding and margin are set relative to the width of a parent element.
- The minimum and maximum width of elements can be set using `min-width` and `max-width`.
- The minimum and maximum height of elements can be set using `min-height` and `max-height`.
- When the height of an image or video is set, then its width can be set to `auto` so that the media scales proportionally. Reversing these two properties and values will also achieve the same result.
- A background image of an HTML element will scale proportionally when its `background-size` property is set to `cover`.
____________________________________________________________________________________________________________________
	
# Responsive Web Design - Media Queries

Like we mentioned earlier, because websites can be viewed on various devices with their own resolutions/screen sizes its important that websites are able to resize and reorganize their content to best fit screens of any size.

When they dont, the content may look odd or become indecipherable. When a website responds to the size of the screen its viewed on, it's called a *responsive* website.

This means that they are able to respond in a change in screen size and adapt the content so that users can access it.

## Viewport Meta Tag

We've covered how to create responsive web designs with CSS, however in order to enable this responsive CSS to work we need to be familiar with the HTML viewport meta tag.

The *viewport* is the total viewable area for a user which varies depending on the device.

Based on the viewport, the `<meta>` tag is used to instruct the browser on how to render the webpage's scale and dimensions. For example, say a web page is 960px wide but the device screen is only 320px wide. When we add the `<meta>` tag to the HTML, the webpage will squish the content down until it is 320px.

We place the `<meta>` tag inside of the HTML `<head>` element.

```
<!DOCTYPE html> 
<html lang="en"> 
  <head> 
    ...
    <meta name="viewport" content="width=device-width, initial-scale=1">
    ...
  </head> 
```

- `name="viewport"` tells the browser to display the wbe page at the same width as its screen.

- `content` defines the values for the `<meta>` tag including `width` and `initial-scale`.

- `width=device-width` is a key-value pair that controls the size of the viewport; it sets the width of the viewport to equal the width of the device.

- `initial-scale=1` sets the inital zoom level

## Media Queries

CSS uses *media queries* to adapt a website's content to different screen sizes by detecting the size of the current screen and applying different CSS styles depending on the width of the screen.

```
@media only screen and (max-width: 480px) {
  body {
    font-size: 12px;
  }
}
```
The example above defines a rule for screens smaller than 480px which is approximately the width of many smartphones in landscape orientations.

- `@media` this keyword begins a media query rule and instructs the CSS compiler on how to parse the rest of the rule

- `only screen` indicates what types of devices should use this rule. `screen` is the media type always used for displaying content, no matter the type of device. The `only` keyword is added to indicate that this rule only applies to one media type: `screen`.

- `and (max-width : 480px) is known as the *media feature* and instructs the CSS compiler to apply the CSS style to devices with a width of 480px or smaller. *Media features* are the conditions that must be met in order to render the CSS within a media query.

- The CSS rules that we nest inside of the media query's curly braces tell the compiler how to style the content when the query has been met. In the example above, the font size will be set to 12px if the screen is 480px or smaller.

## Range

We can target specific screen sizes with multiple height and width media features. `min-width`, `max-width`, `min-height`, and `max-height` can be used in this case.

```
@media only screen and (min-width: 320px) and (max-width: 480px) {
    /* ruleset for 320px - 480px */
}
```

The example above would only apply its CSS rules when a screen's width is between 320px and 480px. Also notice that we can chain the requirements together using multiple `and` keywords.

We can also separate them into two individual rulesets:

```
@media only screen and (min-width: 320px) { 
    /* ruleset for >= 320px */
}
 
 
@media only screen and (min-width: 480px) { 
    /* ruleset for >= 480px */
}
```
The first media query in the example above will apply CSS rules when the size of the screen meets or exceeds 320 pixels. The second media query will then apply CSS rules when the size of the screen meets or exceeds 480 pixels, meaning that it can override CSS rules present in the first media query or apply additional CSS rules that are not already present in the first.

Both examples above are valid, and it is likely that you will see both patterns used when reading another developer’s code.

## Dots Per Inch (DPI)

We can also target media feature by screen resolution. For users with higher resolutions we probably want to supply higher resolution media, like images or videos.

To do so we can use `min-resolution` and `max-resolution` media features. These accept a resolution in either dots per inch (dpi) or dots per centimeter (dpc).

```@media only screen and (min-resolution: 300dpi) {
    /* CSS for high resolution screens */
}
```
This targets high resolution screens by making sure the screen resolution is at least 300 dots per inch.

## And Operator

We use the `and` operator to chain multiple media feature requirements together. Previously, we used to to chain `min-width` and `max-width` together but we can also use it to chain properties like `max-width` and `min-resolution` together as well. For example:

```
@media only screen and (max-width: 480px) and (min-resolution: 300dpi) {
    /* CSS ruleset */
}
```
We can use the `and` operator to chain together as many media features as necessary.

## Comma Separated List

If we only need *one* of multiple media features in a media query msut be met, media features can be separated in a comma separated list.

For example, if we needed to apply a style when either

- The screen is more than 480px wide
**OR**
- The screen is in landscape mode

We could use 

```
@media only screen and (min-width: 480px), (orientation: landscape) {
    /* CSS ruleset */
}
```
Note that the second media feature is `orientation`, which detects if a page has more width than height. If its wider than it is tall, then its considered `landscape` and if its taller than it is wide than it is `portrait`.

## Breakpoints

We know *how* to use media queries to apply CSS rules based on screen size and resolution, but how do we know *what* queries we should set?

The point at which media queries are set are called *breakpoints*. Breakpoints are the screen sizes at which your web page does not appear properly. For example, if we want to target tablets that are in landscape orientation, we can create the following breakpoint:

```
@media only screen and (min-width: 768px) and (max-width: 1024px) and (orientation: landscape) {
    /* CSS ruleset */
}
```

However, it would be impractical to set breakpoints for every device imaginable because there are so many and there are new devices constantly being released.

Therefore, it is best practice to resize your browser to view where the website naturally breaks based on its content. The dimensions at which the layout breaks or looks odd become your media query breakpoints, and with this information we know what media queries to use in order adjust the CSS styling.

By observing these breakpoints we can create the best possible experience on a project-by-project basis, rather than forcing every project to fit a certain screen size. Different projects have different needs and so creating a responsive design should be no different.

Consult [this list](https://content.codecademy.com/courses/freelance-1/unit-5/screen-sizes.png?_gl=1*g9mb9q*_ga*Mzg2MDEyNTUuMTY1NDEyMDYwOQ..*_ga_3LRZM6TM9L*MTY2OTY4MDgwOC4xMDkuMS4xNjY5NjgzMTEwLjYwLjAuMA..) of breakpoints by device widths for reference when testing your website to make sure it looks great across a variety of devices.

## Summary

- When a website responds to the size of the screen it’s viewed on, it’s called a *responsive* website.
- Writing *media queries* is how we apply different CSS styles depending on the dimensions of the screen being used. I.e. we query if a screen meets certain requirements and if it does then the CSS is applied.
- Adding the viewport `<meta>` tag to our code allows us to control the width and scaling of the viewport so that it’s sized and scaled correctly on all devices.
- Media queries require *media features*. Media features are the conditions that must be met to render the CSS within a media query.
- Media features can detect many aspects of a user’s browser, including the screen’s width, height, resolution, orientation, and more.
- The `and` operator requires multiple media features to be true at once.
- A comma separated list of media features only requires one media feature to be true for the code within to be applied.
- The best practice for identifying where media queries should be set is by resizing the browser to determine where the content naturally breaks. Natural breakpoints are found by resizing the browser.
____________________________________________________________________________________________________________________

# Digital Accessibility

What is accessibility? This refers to designing devices, prodcuts, and environments so that individuals with disabilities or sensory ipairments can successfully use the device or product.

This is in compliance with the ADA, Americans with Disabilties Act, which madates that publica nd private spaces be made accessible to people with disabilties that include but are not limited to

- Sensory impairments
- Cognitive impairments
- Phsyical limitations

So then, what is digital accessibility? This specifically refers to accessibility within digital media but is not much different from the general idea of accessibility. 

However, the requirements are very different. Some examples include, but are not limited to

- Screen readers that parse a website for a user with visual impariments
- Videos on websites are closed-captioned for individuals with hearing impairments
- Images include "alt text" for individuals with visual impairments
- Websites must be navigable by keyboard for users who may not be able to operate a mouse

This covers only a brief subset of how websites and mobile apps must incorporate digital accessibility, for more information and the complete list of all guidelines refer to the [web content accessibility guidelines 2.1](https://www.w3.org/TR/WCAG21/)

## ARIA

ARIA stands for Accessible Rich Internet Applications and refers to the guidelines that must be followed to create webpages that are ADA compliant and accessible for people with sensory, cognitive, or physical impairments.

## Semantic HTML Elements

Semantic HTML elements help people who use screen readers. For example, we know that a `<header>` element is supposed to contain introductory and navigational elements like a logo, links, and/or a search bar. 

We *could* create `<div class="header">` but this would not be of help for people who use screen readers.

For a complete list of semantic HTML elements, [click here](https://developer.mozilla.org/en-US/docs/Web/HTML/Element).

## ARIA Role

Text on a web page can communicate different types of information. Some text may make up the main content of the page, other text may describe navigation icons, still other text might describe input fields or menus. It can be challenging to place text in the context of a web page without knowing where it is positioned or the type of information it is meant to communicate.

We can use the HTML attribute `role` to help give context to web page information. The value of an element's role attribute changes how a screen reader communicates the element.

For example, we can use `role="complimentary"` to let the screen reader know that the information contained in this element is *complimentary*(or supporting) to the information that is being read at the moment. It helps users of screen readers identify the relationship between the sections of a page.

[Here](https://www.w3.org/TR/html-aria/#allowed-aria-roles-states-and-properties) is a list of all acceptable ARIA roles.

## ARIA Role: Presentation

When a screen reader comes across HTML tags it reads the tag out loud every time the tag is encountered. This poses a problem for things like HTML list tags because of how many times we have to use `<ol>`, `<ul>` and/or `<li>`.

We can instruct screen readers to skip reading unnecessary element tags by setting the `role` attribute value to `presentation`.

The `presentation` role skips over element tags and their necessary children. So when we give the `role="presentation"` attribute to a list it will skip reading `<ol>` or `<ul>` and will also skip the `<li>` elements in each list as well.

When we use `role="presentation"` on something like a div, the screen reader will skip reading "div" but it will read the id or class name for the user.

## ARIA Properties

`aria-label` can give the screen reader additional information to read out loud to the user. For example, if we have an image of some artwork and the artist's name underneath it - to a non-visually impaired person it's obvious that this is the name of the artist. 

```<img src="#" alt="A painting of the Shenandoah Valley"/>
<p>Armand Cabrera, 2010</p>
```

However, for someone who uses a screen reader they may be a bit confused without any added context. Thats where `aria-label` comes in.

```
<img src="#" alt="A painting of the Shenandoah Valley"/>
<p aria-label="Artist">Armand Cabrera, 2010</p>
```

For a complete list of ARIA properties [click here](https://developer.mozilla.org/en-US/docs/Web/Accessibility/ARIA/ARIA_Techniques)

## Alt Attribute

Some HTML elements have a built-in attribute called `alt` that works like `aria-label` but has added functionality.

The `alt` attribute is used to describe an image or several other elements. A screen reader will read this value outloud AND this value will also be what is displayed if the element cannot be loaded/rendered. 

`aria-label` will never be displayed on the screen and is a better choice for elements that do not support the `alt` attribute.

When using the `alt` attribute you should adhere to these conventions:

1. the value shoud concisely describe the image
2. for images that are also `<a>` elements, the `alt` attribute should describe the source that the link targets
3. if an image conveys no information, such as a decorative border, the `alt` attribute should be empty but never omitted
4. if the image is described with text that is near the image, do not duplicate the description in the `alt` attribute and just leave it empty.
5. the value of an `alt` attribute should be no more than 150 characters

## Summary

- Use semantic HTML elements whenever possible to allow screen reader users to navigate your website more easily
- The `role` attribute is used to communicate information about the role of specific elements
- `role="presentation"` allows a screen reader to skip markup elements that don't directly contain useful information
- `aria-label` and other ARIA properties can be used to help users perceive information that is communicated visually but not through text
- the `alt` attribute should be added to every image element - and all other elements that support it - instead of `aria-label` and should be a useful description of the image.
