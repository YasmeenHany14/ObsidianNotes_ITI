---
notion-id: 976cf491e5dc4c939d59d05676b51754
---
[[00-HTML|00-HTML]]
[[CSS|CSS]]
[[SCSS]]
[[Java Script]]
[[01_ITI_courses/Essentials/Frontend/HTML-CSS/TypeScript|TypeScript]]
[[Angular Notes]]
  
https://marketplace.visualstudio.com/items?itemName=standard.vscode-standard
  
![[image 48.png]]
  
# Naming Conventions:
1. Use 2 spaces indentation
2. Link parent and child with a common word (html)
3. Use single hyphen except for modifier classes??
4. start classes with js styling with js ex) js-list-block
    
	![[image 1 25.png]]
    
  
  
# SASS Maps
  
  
  
# Grid anatomy
A grid always starts with a container, which provides horizontal padding and maximum width
A row uses flex box and negative margins for aligment and offsetting column gutters
Column uses horizontal padding as gutters, different width at different break points.
  
  
![[image 2 22.png]]
  
![[image 3 15.png]]
  
![[image 4 12.png]]
  
  
drop down items block display
overflow y make before element disappear
avatar icons cut from sides
  
  
  
# Template-driven VS Reactive forms
![[image 5 8.png]]
## Template-driven
- Most logic/work is done in the template
- For form control, there are special css class, angular manages and adds automatically, to help track control status
	- ng-pristine ⇒ if it is added, means that the input field did not revieve any input from user yet
	- ng-valid ⇒ control is valid
	- ng-invalide ⇒ tells that control is not valid
	- ng-touched ⇒ tells that user touched this control
	- ng-untouched
- We can use these classes to add validation styles.
![[image 6 7.png]]
  
  
## Reactive forms