# validator 

## custom validation 
* hello ever one 


Angular uses directives to match these attributes with validator functions in the framework. Every time the value of a form control changes, Angular runs validation and generates either a list of validation errors that results in an INVALID status, or null, which results in a VALID status.
ehere is the matter we need tpo do it as soon as possible 
### required 
   <input type="text" id="name" name="name" class="form-control"
                required minlength="4" appForbiddenName="bob"
                [(ngModel)]="actor.name" #name="ngModel">
          <div *ngIf="name.invalid && (name.dirty || name.touched)"
              class="alert">
            <div *ngIf="name.hasError('required')">
              Name is required.
            </div>
            <div *ngIf="name.hasError('minlength')">
              Name must be at least 4 characters long.
            </div>
            <div *ngIf="name.hasError('forbiddenName')">
              Name cannot be Bob.
            </div>
          </div>

### length  

The <input> element carries the HTML validation attributes: required and minlength. It also carries a custom validator directive, forbiddenName. For more information, see the Custom validators section.

name ="ngModel" exports NgModel into a local variable called name. NgModel mirrors many of the properties of its underlying FormControl instance, so you can use this in the template to check for control states such as valid and dirty. For a full list of control properties, see the AbstractControl API reference.

The *ngIf on the <div> element reveals a set of nested message divs but only if the name is invalid and the control is either dirty or touched.

Each nested <div> can present a custom message for one of the possible validation errors. There are messages for required, minlength, and forbiddenName.
### method 

A function that receives a control and synchronously returns a map of validation errors if present, otherwise null. interface ValidatorFn { (control: AbstractControl<any, any>): ValidationErrors | null }
### min  
The <input> element carries the HTML validation attributes: required and minlength. It also carries a custom validator directive, forbiddenName. For more information, see the Custom validators section.

name="ngModel" exports NgModel into a local variable called name. NgModel mirrors many of the properties of its underlying FormControl instance, so you can use this in the template to check for control states such as valid and dirty. For a full list of control properties, see the AbstractControl API reference.

The *ngIf on the <div> element reveals a set of nested message divs but only if the name is invalid and the control is either dirty or touched.

Each nested <div> can present a custom message for one of the possible validation errors. There are messages for required, minlength, and forbiddenName.
Now, the limit of the angular resolution refers to the smallest value of this angle, up to which the two objects can be distinguishable by the optical instrument
### max  

<input type="text" id="name" name="name" class="form-control"
                required minlength="4" appForbiddenName="bob"
                [(ngModel)]="actor.name" #name="ngModel">
          <div *ngIf="name.invalid && (name.dirty || name.touched)"
              class="alert">
            <div *ngIf="name.hasError('required')">
              Name is required.
            </div>
            <div *ngIf="name.hasError('minlength')">
              Name must be at least 4 characters long.
            </div>
            <div *ngIf="name.hasError('forbiddenName')">
              Name cannot be Bob.
            </div>
          </div>
