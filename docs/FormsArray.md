Html code
``` 
 

<hello name="{{ name }}"></hello>
<p>
  Start editing to see some magic happen :)
</p>
<div [formGroup]="orderForm">
<div formArrayName="items"
  *ngFor="let item of orderForm.get('items').controls; let i = index;">
  <div [formGroupName]="i">
    <input formControlName="name" placeholder="Item name">
    <input formControlName="description" placeholder="Item description">
    <input formControlName="price" placeholder="Item price">
  </div>

  Chosen name: {{ orderForm.controls.items.controls[i].controls.name.value }}
</div>
</div>
<button (click)="addItem()">Add</button>
```
Ts code 
```
import { Component } from '@angular/core';
import { FormBuilder, FormGroup, FormArray, FormControl, Validators } from '@angular/forms';

@Component({
  selector: 'my-app',
  templateUrl: './app.component.html',
  styleUrls: [ './app.component.css' ]
})
export class AppComponent  {
  orderForm: FormGroup;
items: FormArray;

constructor(private formBuilder: FormBuilder) {}

ngOnInit() {
  this.orderForm = new FormGroup({
    items: new FormArray([])
  });
}

createItem(): FormGroup {
  return this.formBuilder.group({
    name: '',
    description: '',
    price: ''
  });
}

addItem(): void {
  this.items = this.orderForm.get('items') as FormArray;
  this.items.push(this.createItem());
}
}

```
app.modules.ts

```
import { NgModule } from '@angular/core';
import { BrowserModule } from '@angular/platform-browser';
import { FormsModule, ReactiveFormsModule } from '@angular/forms';

import { AppComponent } from './app.component';
import { HelloComponent } from './hello.component';

@NgModule({
  imports:      [ BrowserModule, FormsModule, ReactiveFormsModule ],
  declarations: [ AppComponent, HelloComponent ],
  bootstrap:    [ AppComponent ]
})
export class AppModule { }

```