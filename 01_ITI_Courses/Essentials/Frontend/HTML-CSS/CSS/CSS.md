---
notion-id: 103ba0f393fd808bb135e8420583f64e
---
[[Setting style]]
  
  
https://jigsaw.w3.org/css-validator/
  
![[image 7 7.png]]
![[image 1 1 1.png]]
  
[[Display Grid]]
[[Flex box]]
[[Colors and Typography]]


# Syntax
selector {
	property: value
}

# Selectors

## Simple selectors
1. Element selectors
	Select all elements with a specific tag and apply style to them
2. ID selectors
	Select by element id
3. Inline selectors
	Write styles inline with each html tag
4. Class selectors
``` css
h2 {
	bg-color="red";
}
#myid {
}

.myclass {
}


```
![[Pasted image 20261004201825.png|353]]

## Complex Selectors
![[Pasted image 20261004202123.png|342]]
1. Universal Selectors
	Using wildcards
	Low specifity
	Usually written at the start of the page
2. Multiple and combination selector
3. Attribute selector
	`[width]`
4. pseudo elements
		::after ::before ::first-letter ::first-line ::selection
5. pseudo classes
	:hover
	``` CSS
	h1, h2, h3 {
		color: green;
	}
	
	//space selector
	div p { // select p inside a div even if not directly
		color: green;
	}
	
	// direct child
	div > p {
		color: green;
	}
	
	// selects all p elements that are immediatly after a div as a sibling (only first sibling )
	div + p {
	}
	
	// selects all p elements that are siblings of div elements
	div ~ p {
	}
	
	//attr
	div[width=105px]
	[width ^="10"] select all elements with width that starts with 10
	[width $= "5px"] select all elements with width ends with 5px
	[width *= "0"] select all elements with width containing 0 anywhere
	
	[type= ~= "ccc"] select all elements with attr type of value strictly equals ccc
	
	[type |= "ccc"] select all elements with attr type of value starts with ccc or ccc- 
	
	```

# CSS Properties
![[Pasted image 20261004204211.png]]


**Percentage height/width and parent containers**
When `height` or `width` is set as a percentage, the element sizes itself relative to its parent container.

For `height`, this only works if the parent has a definite height (a fixed value, or a percentage that itself resolves up the chain). If the parent's height is dynamic (`auto`, i.e. determined by its content), the child's percentage height is ignored and behaves like `auto`.

**Why:** the parent's height would depend on the child, and the child's height would depend on the parent, which is circular.

**Width is different:** block elements get their width from the available space, not their content, so percentage widths usually work.

**Fixes:** give the parent an explicit height, chain `height: 100%` up from `html`/`body`, use viewport units (`vh`), or use flexbox/grid (`flex: 1`), which is usually the best option.


box-sizing: border-box; => includes padding and border size to the container set width

![[Pasted image 20261005120345.png]]
vertical: takes max margin, horizontal sums margins

visibility hidden vs display hidden
visibility hidden still reserves object space even though it's now visible
display none hides the element and doesn't reserve space for it (doesn't load in dom)


shorthand props
	border: width style color
	padding/margin: top right bottom left
	or          : top+bottom right+left
	border-width: same
	border-color: color style;   (black transparent)
	border style: solid dashed groove dotted; (style for each side)
	![[Pasted image 20261005142950.png]]
	![[Pasted image 20261005151353.png|372]]![[Pasted image 20261005151435.png|369]]



## CSS Positioning
1. Static = inherited = initial
2. Absolute => relative to the body/ `<html>` / removes element from document flow unless it's parent is static position
	Positioned relative to it's parent incase parent has a position
3. Fixed => relative to the viewport 
	Removes the element from page layout/natural document flow
4. Relative => relative to its normal position
	Has no impact on the element if we dont change any of the directions values
		For this reason it's best to pair with position absolute(child)
5. Sticky => sticks in the same place even while scrolling until we scroll to a certain point
	One of it's uses is navbar
![[Pasted image 20261005162423.png|364]]
* z-index prop does not work if element has position: static

float allows other elements to float around it 


## CSS Layout
![[Pasted image 20261005180502.png|361]]


![[Pasted image 20261005215104.png]]