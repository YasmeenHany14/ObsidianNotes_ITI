---
notion-id: 104ba0f393fd80c2819bcba92e7831d5
---
## Attribute selector
- Setting style for a specific element based on it’s attribute
```html
<img src="btats"/>
<!-- Now we want to set style to not only any img element,
 but any ing element with that src attribute -->
<style>
	img[src"btats"] {
	 # style goes here
	}
</style>
```
  
## Selector list
- Apply style to more that one element
    
	```html
	<style>
		h1, h2 {
			# apply style to h1, h2
		}
	</style>
	```
    
  
## Combinators
- Create a rule that targets a specific child of a specific element
    
	```html
	<style>
		.first-class>p {
			# apply style to p elements inside .first-class class
		}
	</style>
	```
    
  
### Display Property
1. Block ⇒ Takes the whold block
2. Inline ⇒ Make inline element - in this case the width property gets ignored ==(why?)==
3. Inline-block ⇒ To have inline while having control over properties like width and stuff.
  
### Inheritance
- Any properties about size doesn’t get inherited by the child
  
### Background
- Change bg color using hex code - RGB
  
### Image
  
  
### Repeat