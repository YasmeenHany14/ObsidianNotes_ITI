---
notion-id: b6a3437123b44706ba206cd2649bb074
---
- Instructions that start with `!` means they are processing instructions and not part of the document
## DOCTYPE
- Data to tell the browser what html version you are using building the website
- Previously it was structured in such a way that follow some standards.
- `<!DOCTYPE html>` → html 5
  
## HTML
- Acts as the root of the document.
- `<html> </html>`
- Important for browsers to know the root of the document.
  
## HEAD
- `<head> </head>`
- Contains extra metadata and information about processing the document that we can provide to the browsers.
[[HEAD Tags]]
## BODY
- `<body> </body>`
- Contains the content to be displayed
[[BODY Tags]]
  
We can validate our HTML code using W3C Markup validation service.
  
[[Media]]
[[Forms]]
https://developer.mozilla.org/en-US/docs/Glossary/Semantics
alt + shift + arrow → copy line


## Links types
### File links 
	<a href="remote or local file"></a>
	<a 
 * In referencing local files, we can use absolute or relative path
 * relative path is preferred as absolute can change from one device to another

### Anchors
* Move between sections in the same page
	`<a href="#test"> </a>`
	`<span name="name">`
* We can go to a specific section of another page by combining relative path + section anchor at the end

### Email
	`<a href="mailto:yasmeen@btats.com?subject=aaa&body=btats-is-so-cool">`