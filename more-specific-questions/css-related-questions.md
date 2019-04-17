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

visibility: hidden - hides the element, but it still takes up space in the layout.

display: none - removes the element from the document. It does not take up any space. 

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



