form and validation 
# forms 

app.html 
```

<form [formGroup]="form">

<label>firstname </label>
<input 
type="text"
placeholder="firstname"
formControlName="firstname"
><br>
<div class="red" *ngIf="form.get('firstname')?.touched && form.get('firstname')?.errors?.['required']">
  First name is required.
</div>

<div class="red" *ngIf="form.get('firstname')?.errors?.['minlength']">
  Firstname must be at least 3 characters long.
</div>

<label>lastName</label>
<input 
type="text"
placeholder="lastname"
formControlName="lastname"
>
<div class="red" *ngIf="form.get('lastname')?.touched && form.get('lastname')?.errors?.['required']">
  lastname is required 
</div>
<br>

<label>textme</label>
<textarea formControlName="textme"></textarea><br>

<label>gender:</label>
<div class="aligment">

  <label>male</label>
  <input 
  type="checkbox"
  formControlName="male"
  >
  <label class="right">Female</label>
  <input 
  type="checkbox"
  formControlName="Female"
  >
</div><br>

<label class="top">patientdetails:</label>
<div class="aligment">


<label>inpatient</label>
<input 
type="radio"
value="inpatient"
formControlName="patient"
>
<label class="right">outpatient</label>
<input 
type="radio"
value="outpatient"
formControlName="patient"
>
</div>

</form>

<button (click)="clickme()">save deatils</button>
```

app.ts
```
import { CommonModule } from '@angular/common';
import { Component, inject } from '@angular/core';
import { FormBuilder, FormControl, FormGroup, FormsModule, ReactiveFormsModule, Validators } from '@angular/forms';
import { RouterOutlet } from '@angular/router';
import { ChildComponent } from './child/child.component';

@Component({
  selector: 'app-root',
  standalone: true,
  imports: [RouterOutlet,CommonModule,ReactiveFormsModule,FormsModule,ChildComponent],
  templateUrl: './app.component.html',
  styleUrl: './app.component.css'
})
export class AppComponent {
  title = 'forms';
  form:FormGroup
  array:any[]=[]

  private fb = inject(FormBuilder)

  constructor(){
this.form=this.fb.group({
  firstname:new FormControl('',[Validators.required,Validators.minLength(5)]),
  lastname:new FormControl('',[Validators.required,Validators.maxLength(6)]),
  textme:new FormControl(),
  male:new FormControl(),
  Female:new FormControl(),
  patient:new FormControl()
})
  }


  clickme(){
    this.form.markAllAsTouched()
    if(this.form.valid){
      console.log(this.form?.value);
      this.array = [...this.array, this.form.value]  
      // we need to write in this way beacause the ngchanges will decucte 
      // this.array.push(this.form.value)
      console.log(this.array,'array')
    }
  }
}
```




## patch values in the formcontrol 
```
       dateOfDeath:this.list.expiryInfo[0].dateOfDeath? new Date(this.list.expiryInfo[0].dateOfDeath):null,-- when the date is to be modified 
        preliminaryCauseOfDeath:   this.list.expiryInfo[0].preliminaryCauseOfDeath,
        isExpired:    this.list.expiryInfo[0].dateOfDeath?true:false -- ternary operator---  
```

### patch value by  length

```
	  let signoutData = (this.signOutdata && this.signOutdata?.length > 0) ? this.signOutdata[0] : null;
this.signOutForm.patchValue({
  signOutDate: signoutData?.signOutDateTime? new Date(signoutData.signOutDateTime):null,
  reason:signoutData?.signOutReason?signoutData.signOutReason:null
})
```