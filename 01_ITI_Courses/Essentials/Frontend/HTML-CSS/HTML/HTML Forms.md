---
notion-id: 101ba0f393fd80ff8b55cd69ee73248b
---
- `<form> </form>`
- We can put div or anything inside a form
https://developer.mozilla.org/en-US/docs/Learn/Forms/How_to_structure_a_web_form
# Form Elements
## Input
- `<input>`
- Self closing tag
- Used to input data to the form
### Basic input categories:
1. Single line text
	1. Could be (Text/search, Hidden, Password)
2. Multiple line text
3. Selection ⇒ checkbox, sliders, etc
### Input Attributes:
1. Type ⇒ Used to specify the input data type
	ex) _(text, password, submit, reset, radio, checkbox, URL, email, telephone, number, date, time, file…)_
		There is a type called image => `<input type="image" src="image location">`
	
2. Required ⇒ Mark a field as required
3. Name => _used to define the name of the input field_
4. Placeholder ⇒  _used to define a short hint for the input field_
5. Value ⇒ _used to define the value of the input field (default value)_

To associate a label with an input field, both must share the same id and not the same ==name==.

When a form is submitted, the **name** attribute is used as the key in the key-value pair sent to the server. 

The **name** attribute allows you to easily access form elements using JavaScript

### Input Types
1. Hidden ⇒ _used to define that the input field is hidden_
	- Why use hidden attribute?
		- In some cases there are some additional data that needs to be sent along with form data which the user doesn’t need to see.
2. Reset ⇒ _reset field resets the form_
3. Readonly ⇒ _used to define that the input field is read-only (cannot be changed)_
	- Data gets sent in request body
4. Disabled ⇒ _used to define that the input field is disabled (cannot be used)_
	- Gets grayed out - Data doesn’t get sent in request body
5. Autofocus ⇒  _used to define that the input field should automatically get focus when the page loads_
6. Minlength - Maxlength ⇒ _Input length_

  

### Specific input types

1. Color ⇒ _used to open a color picker wheel_
2. Range ⇒ _used to define a range of values for the input field_
	- Accepts the following: (min, max, step, value→start value
3. Number ⇒ _used to define a numeric input field - Doesn’t accept text_
	- Accepts the following: (min, max, step, value,
4. File ⇒ _allows the user to select a file to be uploaded_
	- Accepts the following attributes:
		- Accept ⇒ _used to define the types of files that the file input field can accept_
		- Multiple ⇒ _used to define that multiple files can be selected for upload_
5. URL ⇒ _used to define a URL field_
6. Telephone ⇒ _tel -used to define a telephone field_
7. Search ⇒ _used to define a search field_
### Time and Date types:
1. Month ⇒ _used to define a month field in a year-month format_
2. Week
3. Time ⇒ _used to define a time field in a 24-hour format_
4. date ⇒ _used to define a date field in a year-month-day format_
  
## Radio and Checkbox
- Radio ⇒ _allows the user to select one option from a group of options_
- Checkbox ⇒ _allows the user to select multiple options_
- They both share the same attributes and works almost the same way except a few notes:
    
	1. Using the `checked` attribute on multiple radio boxes will result in only the last one being selected, but using it on multiple checkboxes will have all of them checked.
    
      
    
 When multiple radio buttons share the same `**name**` attribute, they are grouped together. This means that only one radio button in the group can be selected at a time.
  
  
## Select
- Select ⇒ _used to define a drop-down list_
- To put options inside the drop down list we use the `<option> </option>` tag inside the select tag
- To group multiple options together we the tag <optgroup> </optgroup>
- _optgroup are just used to group the options in the select tag for more organization_
    
	```html
	        <select name="book" id="book">
	          <optgroup label="fiction books">
	            <option value="1"> Book 1</option>
	            <option value="2"> Book 2</option>
	          </optgroup>
	          <optgroup label="romance books">
	            <option value="3"> Book 3</option>
	            <option value="4"> Book 4</option>
	          </optgroup>
	        </select>
	```
    
	### Attributes:
    
	1. Value ⇒ _used to define the value of the option that gets sent when it is selected_
	2. Size ⇒ _used to define the number of visible options in the drop-down list_
	3. Multiple ⇒ _used to define that multiple options can be selected from the drop-down list_
	4. Selected ⇒ _used to define that an option is pre-selected in the drop-down list_
  
## Label
- used to define a label for the input field
- `<label> </label>`
- There are a few ways to associate a label with an input field:
	1. Explicit reference by id
        
		```html
		        <label for="name"> Name</label>
		        <input type="text" name="name" required>
		```
        
	2. Implicit reference by enclosing
        
		```html
		        <label for="name"> Name 
		          <input type="text" name="name" required>
		        </label>
		```
        
  
### Label Attributes:
1. for ⇒  _used to define which input field the label is for_
  
## TabIndex
- Used to specify the tab order to navigate through the form/document (where the form starts and where to go when tab is pressed)
- Tabindex is not a tag but an attribute that can be put inside any element tag
- If you decide to use the tabindex attribute make sure to make it for all elements in the document or at least the fields that are important to fill.
- Helps with better accessibility because not all users use mouses, keyboards, or both.
## Textarea
- Used to define a multi-line text input field
    
	### Textarea Attributes:
    
	1. rows ⇒ _used to define the number of rows in the textarea_
	2. cols ⇒ _used to define the number of columns in the textarea_
	3. wrap ⇒ _used to define how the text in the textarea should be wrapped (soft, hard)_
	4. maxlength ⇒ _used to define the maximum number of characters allowed_
	5. minlength ⇒ _used to define the minimum number of characters allowed_
	6. placeholder
  
## Fieldset
- Used to group related elements in a form
    
	### Elements Inside:
    
	1. Legend ⇒ _used to define a caption for the fieldset element_
	2. Disabled ⇒ _used to define that the fieldset is disabled (cannot be used)_
	3. Form ⇒ _used to define the form the fieldset belongs to_
	4. Name ⇒ _used to define the name of the fieldset_
  
## Datalist
- Used to define a list of pre-defined options for the input field - The same as the select element so what is different?
	- _Datalist allows to type in the input field and it will show the options that match the typed text (searchable)_
- It used together with an input field with the `list attribute` and are associated with each other using the id attribute.
```html
        <label for="book"> Choose book</label>
        <input list="books" name="books">
        <datalist id="books">
          <option value="Book 1">
          <option value="Book 2">
          <option value="Book 3">
          <option value="Book 4">
        </datalist>
```
The `**<datalist>**` element doesn’t support the same functionality as the `**<select>**` element when it comes to having different display and value pairs directly. The `**<select>**` element allows you to have a display text and a different value, but `**<datalist>**` only allows you to set the value that is both displayed and submitted.
However, you can still achieve similar functionality using JavaScript.
# Form Attributes
## Action
- The URI to send the form information to
- If left empty it’s default behavior is to send the data to the current page using query string
## Method
- GET ⇒ Appends the form data to the URL in name/value pairs (QUERY STRING)_
- POST ⇒ Sends the form data to the server in the body of the request_
  
## Enctype
- _used to define how the form data should be encoded when submitting it to the server (application/x-www-form-urlencoded, multipart/form-data, text/plain)_
	- The most used type now days is _application/x-www-form-urlencoded_
  
  
# Form Validation
## Validation and NonValidation Attributes
- Min - Max ⇒ For ranges
- MinLength - MaxLength ⇒ For strings/text
- Required
- Pattern ⇒ Uses regular expression
### Novalidate
- Used to disable the browser's validation of the form
- Usually used in test phase when we want to skip browser validation or when we want to validate the form using javascript.
  
### Target
- Used to define where to open the response from the server (self, blank, parent, top)
	- Blank ⇒ _opens the response in a new window or tab_
	- Self ⇒ _opens the response in the same frame_
	- Parent ⇒ _opens the response in the parent frame_
	- Top ⇒ _opens the response in the full body of the window_