# HTML Related Questions

## What is HTML attribute

## HTML5 aside element

The aside element represents a portion of the document whose content is only indirectly related to the document's main content. Asides are frequently presented as sidebars or call-out boxes.

## Form Validation 

HTML5 introduced a new HTML validation concept called constraint validation. 

HTML constraint validation is based on: 

* HTML Input Attributes - e.g. disabled, max, required
* CSS Pseudo Selectors - e.g :disabled, :valid, :required
* DOM Properties and Methods 

## The difference between attribute and property

Attributes are defined on the HTML markup but properties are defined on the DOM. 

## The difference between cookie, sessionStorage and localStorage

All the above-mentioned technologies are key-value storage mechanisms on the client side. They are only able to store values are strings.

|  | cookie | localStorage | sessionStorage |
| :--- | :--- | :--- | :--- |
| initiator | client or server. Server can use Set-Cookie header | client | client |
| expiry | manually set | forever | on tab close |
| persistent across browser sessions | depends on whether expiration is set | yes | no |
| sent to server with every HTTP request | cookies are automatically being sent via cookie header | no | no |
| capacity | 4kb | 5mb | 5mb |
| accessibility | any window | any window | same tab |

