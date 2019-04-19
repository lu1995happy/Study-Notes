# CSS Related Questions

## Box Model

All HTML elements can be considered as boxes. In CSS, the term box model is used when talking about design and layout. The CSS box model is essentially a box that wraps around every HTML element. It consists of margin, border, padding and context. 

## What are properties of box model

margin &gt; border &gt; padding &gt; content 

## Position

* Static
  * this is the default value, all the elements are in order as they appear in the document
* Fixed 
  * the element is positioned relative to its normal position
* Absolute
  * the element is positioned absolutely to its first positioned parent
* Relative
  * the element is positioned related to the browser window
* Sticky
  * the element is positioned based on the user's scroll position

## Display

* inline
* block
  * it will change the width and height based on the settings, and block the lane for wrapped content
* inline-block
  * it will deal better both has the width and height setting and keep wrapped content in line

## Display: none vs visibility: hidden

visibility: hidden - means that the tag will not appear on the page at all, although you can still interact with it through the DOM. There will be no space allocated for it between the other tags.

display: none - means that unlike display: none, the tag is not visible, but space is allocated for it on the page. The tag is rendered, it just isn't seen on the page. 

## How many px is equal to 1 rem

rem is a new feature for CSS3, which stands for root em. It's equal to the computed value of font-size on the root element, the rem units refer to the property's initial value. This means that 1rem equals the font size of the HTML element, which for most browser has a default value of 16px.

## Pseudo-Class and Examples

The Pseudo-Class is used to define a special state of an element. e.g. a:hover, a:link, a:visited.

## Specificity Rules

* Equal specificity: the latest rule counts
* ID selectors have a higher specificity than attribute selectors
* Contextual selectors are more specific than a single element selector
* A class selector beats any number of element selectors
* The universal selector and inherited values have a specificity of 0

## Responsive Design

* Media query 
  * media query made it possible to define different style rules for different media types. By using media query, we can do responsive web design to handle different devices' viewport. 
* Flexbox 
  * Need a container with attributes display: flex, flex-direction: column/row\(-reserve\), flex-wrap: \(no\)wrap\(-reverse\), flex-flow: setting both the flex-direction and flex-wrap

## Pseudo Class

* It is used to define a special state of an element 
* active, checked, disabled, first-child, link, visited
* Pseudo elements: after, before, first-letter, first-line, selection

## Accessibility

* Test size for different device resolution and user's distance
* Setting line height to make text better readable and visually more appealing
* Add @media block to tweak the styling of elements, like set a static header and hide the ads. 



