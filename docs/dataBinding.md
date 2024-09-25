
## Property Binding
Property binding in Angular binds a component property to a DOM property of an element. This means that you're setting the value of a property on a DOM element, not just the HTML attribute. This is important because DOM properties are often different from HTML attributes and can affect the behavior and state of an element.

Example
```
app.component.ts

typescript
Copy code
import { Component } from '@angular/core';

@Component({
  selector: 'app-root',
  templateUrl: './app.component.html',
  styleUrls: ['./app.component.css']
})
export class AppComponent {
  imageUrl: string = 'https://angular.io/assets/images/logos/angular/angular.svg';
  isDisabled: boolean = true;
}
app.component.html

html
Copy code
<img [src]="imageUrl" alt="Angular Logo">

<button [disabled]="isDisabled">Click Me</button>
```
Explanation:

The [src] property binding sets the src property of the img element to the value of imageUrl in the component. This affects the image displayed.
The [disabled] property binding sets the disabled property of the button element to the value of isDisabled. If isDisabled is true, the button will be disabled.

## Attribute Binding
Attribute binding sets the value of an HTML attribute. This is useful for setting non-standard attributes, such as aria-* attributes, data-* attributes, or any other custom attributes that do not have corresponding DOM properties.
```
Example
app.component.ts

typescript
Copy code
import { Component } from '@angular/core';

@Component({
  selector: 'app-root',
  templateUrl: './app.component.html',
  styleUrls: ['./app.component.css']
})
export class AppComponent {
  ariaLabel: string = 'Submit button';
  dataId: string = '12345';
}
app.component.html

html
Copy code
<button [attr.aria-label]="ariaLabel">Submit</button>
<div [attr.data-id]="dataId">Content</div>

```
Explanation:

The [attr.aria-label] attribute binding sets the aria-label attribute of the button element to the value of ariaLabel. This attribute is used for accessibility.
The [attr.data-id] attribute binding sets the data-id attribute of the div element to the value of dataId. This could be used for storing custom data.


## Key Differences of property  and attr binding 
Scope of Binding:

Property Binding: Directly binds to DOM properties. It changes the actual behavior or state of the element (e.g., enabling/disabling a button, setting the src of an image).
Attribute Binding: Sets HTML attributes, which do not always affect the state of the element. Useful for setting custom attributes or attributes without corresponding DOM properties.
Syntax:

```
Property Binding: Uses the syntax [propertyName]="expression".
Attribute Binding: Uses the syntax [attr.attributeName]="expression".
```
Use Cases:

Property Binding: Use when interacting with DOM properties that influence the state or behavior of an element.
Attribute Binding: Use when you need to set non-standard attributes or when the attribute name does not have a corresponding property on the DOM element.

eg1
```
<button [attr.aria-label]="ariaLabel">Submit</button>
<div [attr.data-id]="dataId">Content</div>
```


### diffrence between property binding and attribute binding 

```
<td [colsan]="colspan2"> data is written here </td> this colsan does work in property binding beacuse this property is not know 
if we add attr to it 
<td [attr.colsan]="colspan2"> data is written here </td> this will work if we use attribute binding
```

## Class Binding
Class Binding with Multiple Classes

Class binding in Angular allows you to dynamically add or remove CSS classes from an element based 
on the value of a component property or expression.
This is particularly useful for conditionally styling elements.

eg1 

```
  NGLASSCONDITION
   [ngClass]="{'disabled': addvisitform.value.isExpired?false:true}" ---- condition based disabled
   
    [ngClass]="{'card':implants.length===0 && !isLoadingImplantDevice}">
```
```
html code 
<button [ngClass]="{ 'primary': isPrimary, 'disabled': isDisabled }">Click Me</button>
 [ngClass]="{'disabled': addvisitform.value.isExpired?false:true}" ---- condition based disabled

css
.primary {
  background-color: blue;
  color: white;
}

.disabled {
  opacity: 0.5;
  cursor: not-allowed;
}

eg2
ts file 
export class AppComponent {
  isActive: boolean = true;
}
html
export class AppComponent {
  isActive: boolean = true;
}
css
.active {
  color: green;
}
```

## Style Binding
In Angular, style binding allows you to set the styles of an element dynamically based on component properties.
You can use it to apply styles conditionally or to bind styles from component variables.
 
You can bind styles directly in the template using square brackets [style.property]
```
html
 
<!-- Component template -->
<div [style.color]="textColor">This text color is dynamic.</div>


// Component class
import { Component } from '@angular/core';

@Component({
  selector: 'app-root',
  templateUrl: './app.component.html',
  styleUrls: ['./app.component.css']
})
export class AppComponent {
  textColor = 'blue'; // The color will be applied to the text
}
```
### Binding Multiple Styles

```
<!-- Component template -->
<div [ngStyle]="{ 'color': textColor, 'font-size': fontSize }">This text has multiple dynamic styles.</div>

// Component class
import { Component } from '@angular/core';

@Component({
  selector: 'app-root',
  templateUrl: './app.component.html',
  styleUrls: ['./app.component.css']
})
export class AppComponent {
  textColor = 'green'; // Dynamic text color
  fontSize = '20px';   // Dynamic font size
}
```
## Events in Angular  
Event binding in Angular is used to handle user interactions or events such as clicks, form submissions, and key presses.
It allows you to listen for events and call methods or perform actions in response.
```
<!-- Component template -->
<button (click)="onClick()">Click me</button>
// Component class
import { Component } from '@angular/core';

@Component({
  selector: 'app-root',
  templateUrl: './app.component.html',
  styleUrls: ['./app.component.css']
})
export class AppComponent {
  onClick() {
    alert('Button was clicked!');
  }
}
```
### Passing Event Data
You can pass event data to the event handler method by including $event in the binding.
```
<!-- Component template -->
<button (click)="onClick($event)">Click me</button>

// Component class
import { Component } from '@angular/core';

@Component({
  selector: 'app-root',
  templateUrl: './app.component.html',
  styleUrls: ['./app.component.css']
})
export class AppComponent {
  onClick(event: MouseEvent) {
    console.log(event); // Log the click event object
  }
}
```
### Types of diffrent events 
 
1. DOM Events
These are native browser events that you can handle directly in Angular:

Click Events: Triggered when an element is clicked.
```
html
Copy code
<button (click)="onClick()">Click me</button>
Mouse Events: Include mouseover, mouseout, mousedown, mouseup, etc.

html
Copy code
<div (mouseover)="onMouseOver()" (mouseout)="onMouseOut()">Hover over me</div>
Keyboard Events: Include keydown, keyup, keypress.

html
Copy code
<input (keydown)="onKeyDown($event)" />
Form Events: Include submit, change, input.

html
Copy code
<form (ngSubmit)="onSubmit()">
  <input (input)="onInput($event)" />
  <button type="submit">Submit</button>
</form>
Focus Events: Include focus, blur.

html
Copy code
<input (focus)="onFocus()" (blur)="onBlur()" />
```
2. Angular Events
These are specific to Angular and are used for component communication and lifecycle management:

Lifecycle Hooks: Events triggered during the component lifecycle, such as ngOnInit, ngOnChanges, ngOnDestroy.
```
typescript
Copy code
import { Component, OnInit, OnDestroy } from '@angular/core';

@Component({
  selector: 'app-example',
  template: `<p>Example component</p>`
})
export class ExampleComponent implements OnInit, OnDestroy {
  ngOnInit() {
    console.log('Component initialized');
  }

  ngOnDestroy() {
    console.log('Component destroyed');
  }
}
```

3. NgModel Change Events: Triggered when the value of an ngModel bound form control changes.

```
html
Copy code
<input [(ngModel)]="model" (ngModelChange)="onModelChange($event)" />
NgForm Events: Events like ngSubmit for form submissions.

html
Copy code
<form (ngSubmit)="onSubmit()">
  <input [(ngModel)]="username" name="username" required />
  <button type="submit">Submit</button>
</form>
```
4. Custom DOM Events
You can also create and dispatch custom DOM events.

Example: Creating and Dispatching a Custom Event
```
typescript
Copy code
// Component class
import { Component } from '@angular/core';

@Component({
  selector: 'app-root',
  templateUrl: './app.component.html',
  styleUrls: ['./app.component.css']
})
export class AppComponent {

  triggerCustomEvent() {
    const event = new CustomEvent('myCustomEvent', { detail: { message: 'Hello!' } });
    window.dispatchEvent(event);
  }

  constructor() {
    window.addEventListener('myCustomEvent', (event: CustomEvent) => {
      console.log(event.detail.message);
    });
  }
}
html
Copy code
<!-- Component template -->
<button (click)="triggerCustomEvent()">Trigger Custom Event</button>
```
## Event Filtering

this is used when we want to do that action when the specific key is pressed 
```
<!-- Component template -->
<input (keydown)="onKeyDown($event)" placeholder="Type something">

// Component class
import { Component } from '@angular/core';

@Component({
  selector: 'app-root',
  templateUrl: './app.component.html',
  styleUrls: ['./app.component.css']
})
export class AppComponent {
  onKeyDown(event: KeyboardEvent) {
    // Filter events to process only the Enter key
    if (event.key === 'Enter') {
      console.log('Enter key pressed');
    }
  }
}
```

eg-2
```
<!-- Component template -->
<button (click)="onClick($event)">Click me</button>


// Component class
import { Component } from '@angular/core';

@Component({
  selector: 'app-root',
  templateUrl: './app.component.html',
  styleUrls: ['./app.component.css']
})
export class AppComponent {
  onClick(event: MouseEvent) {
    // Filter clicks based on the button type (left, middle, right)
    if (event.button === 0) {
      console.log('Left mouse button clicked');
    } else if (event.button === 1) {
      console.log('Middle mouse button clicked');
    } else if (event.button === 2) {
      console.log('Right mouse button clicked');
    }
  }
}
```
## Two way binding
there are two type of 
Using ngModel for Two-Way Binding and 
Formcontrol is also is a 2 way binding this topic is coverd in forms topic
```
<!-- Component template -->
<input [(ngModel)]="name" placeholder="Enter your name">
<p>Hello, {{ name }}!</p>

 // Component class
import { Component } from '@angular/core';

@Component({
  selector: 'app-root',
  templateUrl: './app.component.html',
  styleUrls: ['./app.component.css']
})
export class AppComponent {
  name: string = ''; // This property will be bound to the input field
}


```

 
 
 



