# view child 


In Angular, ViewChild is a decorator that allows you to access a child component, 
directive, or DOM element within a parent component. This is useful when you need to manipulate a child component,
 access its methods and properties, or interact with a template reference variable.
 
 ## Step 1: Create the Child Component
```
 import { Component } from '@angular/core';

@Component({
  selector: 'app-child',
  template: `
    <p>Child Component</p>
    <button (click)="changeMessage()">Change Message</button>
  `,
  styles: [
    `
      p {
        color: green;
      }
    `,
  ],
})
export class ChildComponent {
  message: string = 'Hello from Child Component';

  changeMessage() {
    this.message = 'Message updated from Child Component';
    console.log(this.message);
  }
}
```

## Step 2: Use the Child Component in the Parent Component

```
import { Component, ViewChild, AfterViewInit } from '@angular/core';
import { ChildComponent } from './child.component';

@Component({
  selector: 'app-parent',
  template: `
    <h1>Parent Component</h1>
    <button (click)="updateChild()">Update Child</button>
    <app-child></app-child>
  `,
  styles: [
    `
      h1 {
        color: blue;
      }
    `,
  ],
})
export class ParentComponent implements AfterViewInit {
  @ViewChild(ChildComponent) childComponent!: ChildComponent;

  ngAfterViewInit() {
    console.log(this.childComponent.message); // Access child property after view initialization
  }

  updateChild() {
    this.childComponent.changeMessage(); // Call child method
  }
}
```

# Using ViewChild in the Same Component here using in html to ts 

##app.component.html
```
<h1>ViewChild in Same Component</h1>

<!-- Template Reference Variable -->
<p #paragraphRef>Initial Paragraph Content</p>

<!-- Button to Trigger a Method in TypeScript -->
<button (click)="updateParagraph()">Update Paragraph</button>
```

## app.component.ts
```
import { Component, ViewChild, ElementRef } from '@angular/core';

@Component({
  selector: 'app-root',
  templateUrl: './app.component.html',
  styleUrls: ['./app.component.css']
})
export class AppComponent {
  // Accessing the paragraph element using ViewChild
  @ViewChild('paragraphRef', { static: false }) paragraph!: ElementRef;

  // Method to update paragraph content
  updateParagraph() {
    this.paragraph.nativeElement.textContent = 'Paragraph content updated using ViewChild!';
    this.paragraph.nativeElement.style.color = 'red'; // Change text color
  }
}
```

# view children 
##app.html
```
<h1>ViewChildren Example</h1>

<!-- Multiple Template Reference Variables -->
<p #paragraphRef>Paragraph 1</p>
<p #paragraphRef>Paragraph 2</p>
<p #paragraphRef>Paragraph 3</p>

<!-- Button to Trigger a Method in TypeScript -->
<button (click)="updateAllParagraphs()">Update All Paragraphs</button>

```
## app.ts 

```
import { Component, ViewChildren, QueryList, ElementRef, AfterViewInit } from '@angular/core';

@Component({
  selector: 'app-root',
  templateUrl: './app.component.html',
  styleUrls: ['./app.component.css']
})
export class AppComponent implements AfterViewInit {
  // Accessing multiple paragraph elements using ViewChildren
  @ViewChildren('paragraphRef') paragraphs!: QueryList<ElementRef>;

  // Lifecycle hook to confirm references are available
  ngAfterViewInit() {
    console.log('Paragraph elements:', this.paragraphs);
    this.paragraphs.forEach((paragraph, index) => {
      console.log(`Paragraph ${index + 1}:`, paragraph.nativeElement.textContent);
    });
  }

  // Method to update all paragraph contents
  updateAllParagraphs() {
    this.paragraphs.forEach((paragraph, index) => {
      paragraph.nativeElement.textContent = `Updated Paragraph ${index + 1}`;
      paragraph.nativeElement.style.color = 'blue'; // Change text color
    });
  }
}
```