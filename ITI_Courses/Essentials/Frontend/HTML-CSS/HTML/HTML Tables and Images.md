---
notion-id: 73abca372de74c1e9a620f40dfad0d4b
---
# HTML Tables
### Table Structure
1. Caption ⇒ Telling what this tables shows
2. Header ⇒ The top row of the table describes what data are shown below
3. Body ⇒ Data
4. Footer ⇒ Aggregate or max values
  
### Table Tags
```html
    <table> = table element
    each table has header, body and footer
    <thead> = table header
      <th> = table header - used to define a header cell in the table  - bold and centered
      using tr td will not make the text bold and centered inst
    <tbody> = table body
      <tr> = table row - used to define a row in the table
      <td> = table data - used to define a cell in the table
    <tfoot> = table footer
    <caption> = table caption - used to define a caption for the table
    <colspan> = column span - used to merge two or more columns/cells into a single cell
    search these
    <rowspan> = row span - used to merge two or more rows into a single cell
    <colgroup> = table column group - used to define a group of columns in the table
   
```
![[image 29 1.png]]

### Attributes 
* width, height, rowspan, colspan, also styling attrs like font-color and bg-color on any table level, `align="center", valign="middle"`
* `cellpadding="num"` => space between cells
  
# HTML Images
## Img Tag
- `<img src=”src” alt=”alttext” height=”100” width=”100”>`
```html
    src = source of the image
    alt = alternative text for the image shown when the image is not available
    width = width of the image
    height = height of the image
    srcset = source set - used to define multiple sources for the image
    sizes = sizes of the image
    ex for srcset and sizes:
    <img src="img.jpg"
      srcset="img-2x.jpg 2w, img-3x.jpg 3w"
      sizes="(max-width: 600px) 200vw, 50vw">
```
- There are some special cases where you need to define multiple sources for the same image or define multiple sizes in case of different view ports and stuff
- This allows the browser to make smarter choice about choosing which image to render, how to render it, and how much of space it should take.
* width/height => using both together is not recommended
	* Setting one of them makes the browser optimizes the other one to match the predefined
	* Setting both will make img size fixed which may cause problems with reponsiveness
	* 
## Image Map
* Used to isolate and do operations on specific parts of an image
``` html
<img src="src" usemap="#mymap"/>
<map name="myMap">
	<area shape="circle" coords="35, 35, 35" href="give hyperlink if needed"/> x, y, rad 
	<area shape="rectangle" coords="35, 35" href="give hyperlink if needed"/> x, y
	<area shape="polygon" coords="35, 35, 50, 50" href="give hyperlink if needed"/> x , y unlimited number of times
```

## Picture Tag
- Allows us to select images in a similiar way to the img tag and make smart descions about which picture to use.
- The difference here is that it allows you to select the image type and the browser can also choose based on the image format.