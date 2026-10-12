---
notion-id: 66cf5d49a8434cf68a4a40895cf79923
---
Body contains 6 essential elements:
1. Text
2. Lists
3. Links
4. Tables
5. Images
## Class and id Attributes
- Class used to group a class of items and give them some shared properties.
- Id it unique and used only on one single element.
- We can have an item belonging to multiple classes
    
      
    
## Block and Inline elements
- Understanding the diff between them is important to how the browser is going to put an item in reference for other items.
    
	![[image 32 1.png]]
    
  
![[image 1 7 1.png]]
  ****
## Text Breaking and Whitespace
- `<pre> </pre>`
	- Tells the browser that this element has been pre-formatted and the browser should respect that.
- `<br/>`
	- _br = line break - used to break the line_
- `<hr/>`
	- _hr = horizontal rule - used to define a thematic change in the content_
- `&nbsp;`
	- Character entity, represent a character that is special.
	- Short for Not breaking space, i want you to consider this a space but without breaking to the next line.
- `&lt; &gt;`
	- Less and greater than sign

## Reference Text
- `<sup></sup>`
- `<cite></cite>`
	- Mention the person you took this quote from
- `<abbr></abbr>`
	- Mention what the abbreviation stands for
- <code> </code> or <samp></samp>
	- A block of code
- `<kbd> </kbd> or <var> </var>`
	- ???
- `<blockquote></blockqoute> or <q></q>`
    
	- Standard or block element code
    
	```html
	      <p>
	        <q>Im productive when i eat potatoes</q>
	        </br>
	        <cite> yasmeen, &lt;hany&gt;</cite>
	      </p>
	
	      <p>
	        <!--- here both quote and cite are in the same line after rendering -->
	        <q>Im productive when i eat potatoes</q>
	        <cite> yasmeen, &lt;hany&gt;</cite>
	      </p>
	```
    
  
## HTML Semantics
- Instead of using divs for everything, we can use semantic elements which partition the page into different sections
	1. header ⇒ header of the page
	2. nav ⇒ navigation bar
	3. section ⇒ section of the page
		- Inside a section we can still have divs and other elements.
		- It is used to give more meaning to a specific part of a page.
	4. aside ⇒ side content
	5. article ⇒ article content
	6. footer ⇒ footer of the page
## Headings
- Denote sections of the documents
- From H1 to H6
	- h1 → website name (only this element can use it) - should only appear once per page (This is necessary to help search engines find you)
	- h2 → Chapter title
	- h3 → Story title inside chapter
- Inline elements
  
## Paragraph element
- Block element
	- بيحط مسافة قبل و بعد عشان ميخليش حاجه جمبه و بيعمل فرق سطر بين اللي قبله و اللي بعده
	- Have margin
You can nest paragraphs but it you should not do it because logically it doesn’t make sense because it is a stand-alone block of content, and div is used for this.
  
## Span
- span is an inline element
- span is used to separate a part of the text from the rest of the text so that it can be styled differently
- span doesn’t have any default styling
  
## Div
- Div is a general-purpose element to identify a section of the page.
  
  
## Lists
### Lists tags
```html
    ul = unordered list
    ol = ordered list
    li = list item
    dl = description list - used to define a list of terms and their descriptions
    dt = description term - used to define the term name
    dd = description description - used to define the term description
```

#### Lists example 
``` HTML
<ul type="circle"> type could be defualt/circle/square/...
	<li></li>
</ul>

<ol type="i" start="3"> defaule type here are numbers if not specified
	<li></li>
</ol>

<dl>
	<dt> </dt> (repeat for any number of elements we want)
	<dd> </dd>
</dl>

```

### Lists attributes
```html
    type = type of the list item (1, A, a, I, i)
    reversed = reverse the order of the list
    start = start the list from a specific number (item numbering starts from the number specified)
```
  
## Breadcrumbs
[Types of Breadcrumb Navigation](https://blog.hubspot.com/marketing/navigation-breadcrumbs#:~:text=Breadcrumbs%20are%20a%20navigational%20aid,pages%20above%20the%20current%20page).
https://stackoverflow.com/questions/8060106/what-semantic-html-markup-should-be-used-to-create-breadcrumbs
  
## Attributes
### Global Attributes
- Can be used on any element. ex) class, hidden,
  
### Custom Attributes
- Can be used only on a set of specific elements. ex) <img ref=”” alt=””/>
  
  
## Anchor Tag
- `<a href”link goes here”> link title </a>`
- Inline element
- We have 3 types on anchors:
	1. Source anchor ⇒ using href attribute
	2. Named anchor ⇒ using name attribute
	3. Implicit anchor ⇒ using id attribute ⇒ `<a href”#idname”></a>`

![[Pasted image 20261004190433.png]]
  
We can reference implicit anchor in another document, by using the document path followed by the implicit anchor syntax
```html
<li class="breadcrumb-item"><a href="../index.html\#menu">Menu</a></li>
```
  
### Name Attribute
- `<a name=”name”>`
- The name attribute of the anchor tag can be used to enable users to “jump” to a specific point on a page (jump marker, anchor). This is especially useful with large pages or subdivisions.
### Target Attribute
- Instructions on how destination target should me opened
- `<a href="``[http://www.mypage.com](http://www.mypage.com/)``" target="_blank">Linktext</a>`
	- Target blank means open it in a new tab.
### Title Attribute
- Global
- Gives users an important indication as to where they will be directed to when they click on a link.
- It’s value appear on hovering over the element
![[image 2 4 1.png]]
Title here is Go To Facebook
### Href Attribute
- Source anchor
- Can link to another html page → `<a href”test.html”> link title </a>`
- Can link to a specific element with a specific id or name→ <a href”\#testId”> link title </a>
- Can link to an email → <a href”mailto:testmail@test.com”> link title </a>
More about types:
#### File links 
	<a href="remote or local file"></a>
	<a 
 * In referencing local files, we can use absolute or relative path
 * relative path is preferred as absolute can change from one device to another
#### Anchors
* Move between sections in the same page
	`<a href="#test"> </a>`
	`<span name="name">`
* We can go to a specific section of another page by combining relative path + section anchor at the end
#### Email
	`<a href="mailto:yasmeen@btats.com?subject=aaa&body=btats-is-so-cool">`

### Link Metadata
1. Language
2. Relationship ⇒ `rel`
	- The `rel` attribute specifies the relationship between the current document and the linked document.
	- More about it’s values: [HTML  a rel Attribute](https://www.w3schools.com/tags/att_a_rel.asp#:~:text=The%20rel%20attribute%20specifies%20the,more%20information%20about%20a%20link)
3. Content type ⇒ image, text, ...
4. Access key ⇒ search for it
5. Target



## Img Tag
- `<img src=”” alt=””>`
More about images [[HTML Tables and Images#HTML Images]]
## IFrame
* Frame for internet, it's like making a window to view anything inside
* Can be usually seen with ads
	`iframe width="500", height="500" src="">`
	* Height and width can be written as pixels or percentages
#### Attributes
* height, width
* allow="autoplay; encrypted-media"
* allowfullscreen
* frameborder="0" => any number to set border size


## Text Formatting and Styling
-  `font`
	- Used to add specific size to text elements with attributes
	- `<font size="7" color="green" face="ariel"> Text </font>`
		- we can use hex values for colors instead of names
* `<b>` bold
* `<i>` italic
* `<u>` underline
