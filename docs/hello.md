# hello 

https://firebase.google.com/?gad_source=1&gclid=Cj0KCQjwzby1BhCQARIsAJ_0t5M1_dPrJN7mPWntUXlraXSn1U2mH4Zvr8CG5saqwGfPKEmXin0ldgcaArafEALw_wcB&gclsrc=aw


##
<input type="text" id="name" class="form-control"
                formControlName="name" required>
          <div *ngIf="name.invalid && (name.dirty || name.touched)"
              class="alert alert-danger">
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

###

This form differs from the template-driven version in that it no longer exports any directives. Instead, it uses the name getter defined in the component class.

Notice that the required attribute is still present in the template. Although it's not necessary for validation, it should be retained for accessibility purposes.