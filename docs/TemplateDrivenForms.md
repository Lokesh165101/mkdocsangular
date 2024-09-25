## Template variable is defined with the by # 

this is used to acces element properties , methods directly from the template 
Defining Template Variables
```
<!-- Component template -->
<input #myInput type="text" />
<button (click)="onClick(myInput.value)">Submit</button>
 Accessing DOM Elements
<!-- Component template -->
<input #myInput type="text" />
<p>{{ myInput.value }}</p>
 Accessing Component Methods and Properties
 <!-- Parent Component template -->
<app-child #childComp></app-child>
<button (click)="childComp.doSomething()">Call Child Method</button>
// Child Component
import { Component } from '@angular/core';

@Component({
  selector: 'app-child',
  template: `<p>Child Component</p>`
})
export class ChildComponent {
  doSomething() {
    console.log('Method called from parent component');
  }
}
```
## Using Template Variables with Forms
```
<!-- Component template -->
<form #myForm="ngForm">
  <input name="username" ngModel #username="ngModel" />
  <button (click)="onSubmit(myForm.value)">Submit</button>
</form>
// Component class
import { Component } from '@angular/core';

@Component({
  selector: 'app-root',
  templateUrl: './app.component.html',
  styleUrls: ['./app.component.css']
})
export class AppComponent {
  onSubmit(formValue: any) {
    console.log('Form Value:', formValue);
  }
}
```
