# HTML

## What is HTML data-\* attribute

The data attributes are used to store custom data private to the page or application. The data attributes give us the ability to embed custom data attributes on all HTML elements. The stored data can then be used in the page's JavaScript to create a more engaging user experience \(without any AJAX calls or sever-side database queries\). 

The data attributes consist of two parts:

* The attribute name should not contain any uppercase letters, and must be at least one character long after the prefix "data-"
* The attribute value can be any string

## HTML semantic element

A semantic element clearly describes its meaning to both the browser and the developer. e.g. &lt;form&gt;, &lt;table&gt;, &lt;article&gt;

## HTML5 aside element

The aside element represents a portion of the document whose content is only indirectly related to the document's main content. Asides are frequently presented as sidebars or call-out boxes.

## Form Validation 

HTML5 introduced a new HTML validation concept called constraint validation. 

HTML constraint validation is based on: 

* HTML Input Attributes - e.g. disabled, max, required
* CSS Pseudo Selectors - e.g :disabled, :valid, :required
* DOM Properties and Methods 

## HTML accessibility

* use more semantic HTML
* use correct headings
* alternative text
* declare the language and use clear language
* write good links and link titles

## attribute vs property

Attributes are defined on the HTML markup but properties are defined on the DOM. 

## cookie vs sessionStorage vs localStorage

All the above-mentioned technologies are key-value storage mechanisms on the client side. They are only able to store values are strings.

|  | cookie | localStorage | sessionStorage |
| :--- | :--- | :--- | :--- |
| initiator | client or server. Server can use Set-Cookie header | client | client |
| expiry | manually set | forever | on tab close |
| persistent across browser sessions | depends on whether expiration is set | yes | no |
| sent to server with every HTTP request | cookies are automatically being sent via cookie header | no | no |
| capacity | 4kb | 5mb | 5mb |
| accessibility | any window | any window | same tab |

