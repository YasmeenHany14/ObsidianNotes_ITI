---
notion-id: 21dba0f393fd80628f5ed936f8aeb363
---
[[01_ITI_courses/Essentials/Frontend/Angular/Angular Notes/TypeScript|TypeScript]]
  
```tsx
@Component({
  selector: 'app-exam', component name, usually started by app as a naming convention and prevent collusion
  templateUrl: './exam.html', there is also an inline approach, but not recommended except for super small files, line or two 
  styleUrls: ['./exam.scss'], same as template
  standalone: true, starting angular 19+, this will be true by default, false is used in module used components
  imports: [ 
    CommonModule,
    QuestionCardComponent
  ],
  styles: ''
  template: ''
  providers: [MessageService] Services injected
})
```
  
- Create Components using angular CLI
    
	```bash
	ng generate component header
	ng g c header
	
	ng serve // to run server
	ng start // runs ng serve and??
	```
    
- String interpolation is often used ONLY between tags
    
	```html
	<span> {{ selectedUser.name ]} <span\>
	```
    
  
# General Notes
- We should always check our angular.json file and check if assets and their path are included here
    
	![[image 10 2.png]]
    
  
- For components with no attributes to write in tags, we can shorten them and use just one self closing tag
    
	```html
	<app-header><app-header/> 
	TO
	<app-header/>
	```
    
  
- All properties defined in component.js file are available to access in the template file. (Unless you specify it as private)
    
	```html
	Method 1: string interpolation - Usually used between tags
	<div>
	  <button>
	    <img />
	    <span>{{ selectedUser.name }}</span>
	  </button>
	</div>
	
	Method 2: Property binding - Usually used inside a tag
	<div>
	  <button>
	    <img [src] = "'assets/users/' + selectedUser.avatar" [alt]="selectedUser.name" />
	    here is is used along with constructing a dynamic path
	    <span>{{ selectedUser.name }}</span>
	  </button>
	</div>
	
	```
    
	- In property binding, what is written between the double code is always translated as java script code, whatever you write there, angular will try to find variable/signal name matching what is written.
	- If you wanna write a string instead, you wrap the string inside both double and single quotes ⇒ `"'title'"` or just remove prop binding
- Files in public folder do not need to write path to load them.
- Convert from string to number by adding + in front of the number
  
- Attribute binding
  
- You can use getters instead of calculating value inside the html, like calculating the path in the src attribute
```tsx
get imagePath() {
	return 'path' + this.currentUser.Name;
}
```
  
  
## Changing data dynamically
### Event listeners and Zone JS
- Adding an event listener in angular using declarative code
    
	- Event handlers naming convention: Start it with `on` (Not mandatory, there are other conventions)
    
	```html
	  <button (click)="onUserClick()" >
	```
    
- Next is function body inside component.ts file.
- What makes it work without specifically writing an event listener is:
### Zone JS
- Automatically listens to all possible user events, as well as some other events like timer expiring, when this happens it checks the angular application for any changes to apply to apply them automatically.
    
	![[image 1 4 1.png]]
    
  
- This is not the only way to change data dynamically, this was the standard and only way since angular 2 until signals were introduced
    
	![[image 2 3 1.png]]
    
### Signals
- Special kind of values that tells angular when they change, so angular can change the places where these values are used
```tsx
import { Component, signal } from '@angular/core';
export class UserComponent {
  selectedUser = singal(DUMMY_USERS[randomIndex]); // wrap it
}
```
![[image 3 3 1.png]]
  
  
  
```tsx
export class UserComponent {
  selectedUser = signal(DUMMY_USERS[randomIndex]);
  imagePath = computed(() => "assets/users/" + this.selectedUser().avatar);
  // angular signals
  // angular sets up a subscription to the signal, and whenever the signal changes, the component will re-render
  // here it will be recomputed only whenever selectedUser changes
  // GETTERS
  // getters are used as a cleaner way to access properties/computed values in the template
  // get userName() {
  //   return this.selectedUser.name;
  // }
  //
  }
<!-- state management mechanism in zone js-->
<!-- sets zones around your components, which is invisible grouping mechanism where it listens to all kinds of events that could lead to changes in the ui-->
<!-- whenever such a trigger occurs, it scans all the components in that zones to check whether some data changed to update the UI-->
<!-- this is different from signals, which is more efficient, where it knows when and what exactly changed-->
```
![[image 4 2 1.png]]
- Alternative to use computed funcition
  
## NgIf
![[image 5 1 1.png]]
  
## Class Binding
![[image 6 1 1.png]]
## Accepting input with and without signals
```tsx
export class UserComponent {
//   // defining component properties
//   @Input({ required: true }) avatar!: string; // this marks the property as an input, allowing it to receive data from a parent component
// // exclamation mark (!) indicates that this property will be initialized later, so it can be null or undefined initially
//   @Input({ required: true }) name!: string;
// // example of passing configuration to input properties
  // alternative way to define inputs using the input function of signals
  // both are used the same way in the template except you add () to execute them as a function
  avatar = input.required<string>();
  name = input.required<string>();
  // you cant change their values after they are set, so they are read-only, they can only be changed from the outside
  // get imagePath() {
  //   return `assets/users/${this.avatar}`;
  // }
  imagePath = computed(() => {
    return `assets/users/${this.avatar()}`;
  });
  onSelectUser() {
  }
}
```
  
## Custom Events from child to parent components
- Pass parameter/Notify parent an event happened in the child so it can do something with or without data passed from the child
- For this we use Output Properties
- Just like Input decorators and input method, Outputs can be done by either Output decorator or output method.
	- The difference between how input, output methods work lies in that input actually creates a signal to track it, while output does not and it just creates an event emitter.
```tsx
export class UserComponent {
  // emit an event when the user is selected to any components interested in it
  // @Output() select = new EventEmitter<string>(); // using decorators, specifying type is not mandatory
  select = output<string>(); // alternative way to create an output event emitter
  avatar = input.required<string>();
  name = input.required<string>();
  id = input.required<string>();
  
  onSelectUser() {
    this.select.emit(this.id()); // how data are sent/emitted
  }
}
```
```html
    <li>
      <app-user
        [avatar]="users[1].avatar"
        [id]="users[1].id"
        [name]="users[1].name"
        (select)="onSelectUser($event)" how data are passed
      />
    </li>
```
  
# Rendering dynamic content
## Dynamic List
- Syntax and explanation in ss
![[image 7 1 1.png]]
- This is a new syntax introduced in angular 17, previously the standard was to use ***ngFor**
    
	- `ngfor`is a structural directive that allows us to iterate over a list of items.
	- To use it we:
        
		`import {NgForOf} from "@angular/common";`
        
    
	![[image 8 1 1.png]]
    
## Outputting conditional content
- Not rendering element when they are not needed, (Render on use)
- Use ==if conditions==
	- If selected user is not null, do render what is inside the braces, if not fall back to the else statement
![[image 9 1 1.png]]
  
- Same about it being a new syntax applies to If as well.
- The older standard was to mark the div conditioned with*ngIf
- Else statement was a statement wrapped around a special element,  
	`<ng-template>` , given an id and passed to the else condition to find and execute.
![[image 10 1 1.png]]
  
### Dynamically apply classes
- This is done using class binding.
- Same way we bind properties but here we bind a css class on a condition
`<button [class.active]="selected()" (click)="onSelectUser()" >`
  
  
# Directives
- Start with `ng` prefix
- We can build our own directives
- Directives are just to add extra functionalities to elements (enhancement to elements)
- Almost like components, but unlike components they don’t have templates
	- Components are considered directives with templates
![[image 11 2.png]]
# Filling forms
- Two-way binding feature using `ngModel` directive
	- Meant to get used with inputs so you could keep track of the data with every keystroke and override it if needed
- Two-way binding syntax: `[(ngModel)]="propname"`
	- Cannot be used on properties, not by default.
	- Should be imported `import {FormsModule} from "@angular/forms";`
- The `FormsModule` automatically uses <form> as a selector, and takes complete control of the form using an inside form component which executes instead.
- `<form (ngSubmit)="onSubmitTask()" >` ⇒ Prevent HTML default behavior to call database, and execute an action instead.  
    
### Two-way binding with signals
- The correct way to two way bind a signal is the second one, as adding () means to call the read only function for signals.
![[image 12 2.png]]
# Wrapping components with other components
- If you use a custom made angular component as a wrapper around other HTML elements, it will not keep them, it will replace the wrapped up markup with it’s own markup.
- To keep both content, we use `<ng-content />` element.
	- Acts as a placeholder for the markup wrapped by the component, which helps us merge both content togethr.
	- If we use `<ng-content>` multiple times, angular does not know which goes where
		- For this we use an ng content feature, using selectors to match ng-content with which element to fill
		- For example, here we use `<ng-content select=".icon">` and `<ng-content select=".text">` to differentiate
```html
// Child component
<span> <ng-content /> </span>
<span class="icon"> <ng-content select=".icon" />  </span>
// Parent component
    <button appButton type="submit" class="primary">
      <span> Submit </span> // first one
      <span class="icon">⌲</span> // second one, marked with icon class
    </button>
```
  
- Here is this example, we end up with some duplication, we may want to set icon class from the inside and not outside. To solve this, we can use another angular feature, `ngProjectAs`
- Tell angular hey, treat this as if it is HTML element name icon, and tell ng-content to search for one.
```html
// Child component
<span> <ng-content /> </span>
<span class="icon"> <ng-content select="icon" />  </span>
// Parent component
<button appButton type="submit" class="primary">
  <span> Submit </span>
  <span ngProjectAs="icon">⌲</span> // Project this element as icon element
</button>
```
### Fall back content
- On event of failure to load/provide content, angular ha sa new feature to define fall back content.
- To use it, we use <ng-content> element not as a self closed element
  
  
- Pipes, output transformers, things that transform output in templates
    
	- `<time> {{ task.dueDate | date }} </time>` ⇒ Example of date pipe which will transform date string format into more user friendly way.
	- It can be configured, check documentation for more details.
    
      
    
# Angular Modules
![[image 13 2.png]]
![[image 14 2.png]]
- In modules, we combine components that works with each other instead of importing inside needed components them like how components work.
- Each module should be able to work on its own, if it needs a resource, it should import it itself, and it can’t get it from any parent module.
- We bootstrap only the root module, usually the `app.module` , and inside it we should always import `BrowserModule` module.
- We can import modules inside standalone components and vice versa.
```tsx
@NgModule({
  declarations: [ // content of module
    AppComponent,
    HeaderComponent,
    UserComponent,
  ], // register all components that needs to work together
  bootstrap: [AppComponent], // define base component
  imports: [BrowserModule, TasksModule, SharedModule] // for standalone components, or imported modules.
	exports: []// components that this module users/inheritors can access.
})
```
- Shared Components are usually put in a shared module.
- Pipes are part of `BrowserModule`, But since we can only import it in the main component, they are also available through `CommonModule`, provided by angular
  
# Dependency Injection
![[image 15 2.png]]
![[image 16 2.png]]
![[image 17 1.png]]
  
![[image 18 1.png]]
ctrl shift link to open webstorm javascript debugger
  
  
angular dev tools ⇒ browser extension used to work with angular is dev tools
https://angular.dev/tools/devtools
  
# Extending built-in HTML Elements
- There are many types of selectors, not just element selectors. (The one where we type app-button)
	- Documentation ⇒ https://angular.dev/guide/components/selectors
- For this we use attribute selector.
  
  
  
# RXJS
- A concept introduced by a third party library called RXJS, used by angular internally.
## Observables
- Object that produces and controls a stream of data
- We listen to the values emitted from the observable by subscripting to it
	- Just subscribing wont actually do anything, we need a subscriber to listen to the emitted value, so we subscribe and specify who should listen to this?
	- Subscribe method accepts observer object, with 3 methods:
		- Next ⇒whenever a new value is emitted
		- Complete ⇒ will fire when the observable won’t emit any new values.
		- Error ⇒ handle errors (used with http requests)
	- We should clean subscription on component destroy, to make sure no memory leak happens
- RXJS works with operators, special functions provided by RXJS, to perform operations on observables.
	- These operators are used and executed before value reaches the subscriber, inside the pipe method
- You can’t use pipe without subscribe, because with no subscribers no data will be omited
  
  
### Observable VS Subjects
- Subjects are observables, though you take care of emitting data manually.
- In observables, you usually have some kind of data source to emit the data automatically for you.
  
### Observables VS Signals
![[image 19 1.png]]
![[image 20 1.png]]
- We can convert signal to observable using `toObservable()` method
	- This must be done in places where you can inject values, either in the constructor or as a value in a property
- observables naming convention is adding a $ at the end of the name.
    
	![[image 21 1.png]]
    
- The opposite is also possible, using `toSignal` method
    
	- Observables unlike signals, does not have initial values, so while converting to signal, we can pass an initial value in a configuration object as the second argument
	- ToSignal does the cleanup automatically, unless specified otherwise
    
	![[image 22 1.png]]
    
![[image 23 1.png]]
  
### Creating Observable from scratch
- We use the Observable class provided by RxJs constructor, which we pass a function to it, to define how this observable will behave and emit the values
- The next: method here is different from the one used in the subscribe method, this one defines when and how the values will get emitted, while the other defines how to deal with the emitted values.
![[image 24 1.png]]
![[image 25 1.png]]
- This one here is running forever, because we never defined the behavior to invoke the complete event
![[image 26 1.png]]
- You can use it with http requests, to define observables that are DONE after maybe a request was received
- You can also emit an error event, to invoke it incase you have some logic in the observable that can FAIL.
  
  
## When should we split up components?
- Every component should do only ONE THING (single responsibility), however how you decide this responsibility is up to you.
- For super simple components or very small-scale stuff, better not to split them up much to keep is simple and avoid extra complexity
    
	![[image 27 1.png]]
    
  
## Content Projection
- `<ng-content\>` tag
- we can specify elements / selectors that can fill it using select attribute, we can specify one or many selectors in it
![[image 28 1.png]]
  
```html
<form>
  <app-control label = "Title">
    <input name="title" id="title" type="text" placeholder="Enter ticket title" required />
  </app-control>
  <app-control label = "Request">
    <textarea name="request" id="request" type="text" placeholder="Enter request" rows="3" required ></textarea>
  </app-control>
  <p>
    <button appButton type="submit" class="primary">
      <span> Submit </span>
      <span ngProjectAs="icon">⌲</span>
    </button>
  </p>
</form>
<!--ngProjectAs is to tell Angular to treat the content as if
it had the specified selector, even though it doesn't.
In this case, it allows the second span to be treated as if it had the class "icon",
which is used in the button component's template to style the icon appropriately.-->
```