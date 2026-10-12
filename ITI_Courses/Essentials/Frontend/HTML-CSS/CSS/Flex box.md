---
notion-id: 107ba0f393fd803eb0b8d9b5e28839be
---
- Flex container is all about the relationship between the parent/flex container and it’s children/flex item
- Display: flex;
  
![[image 31 1.png]]
  
  
  
### Flex Grow Factor
- flex-grow
- Give more grow factor to one item over the other items
  
  
### Shrink factor
- Controls how space is distributed when there are no enough items to fit
- Remove extra scpace from the item in that case
### Flex basis
- Sets initial size of a flex item before applying grow and shrink factors.
  
![[image 1 6 1.png]]
  
  
### Justify Content
- Align the flex container items on the main axis which is by default the x axis
- In case of flex column, the main axis is the y axis
- Distribute items with spaces with `space-between` and space around values
  
### Align items
- Align the flex items across the cross axis (the opposite of justify content)
- baseline?
- stretch for the entire cross size of the container (default)
  
### Align self
- Align each item separately from the other flex items
  
  
### Align content
- Used to align multiple lines of the flex container and won't work on a single line
- It works the same as Justify-content except that its axis is always the x axis regardless of the flex direction.
- Effect shows when wrapping 
  
### Gap
- Add space between flex items - doesn’t get applied on the sides.
  
  
content-between


### Flex flow
* Shorthand for flex direction + flex wrap


![[Pasted image 20261005203746.png]]