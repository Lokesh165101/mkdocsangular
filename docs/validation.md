
## validation 

```
  FORMVALIDATION ---  <mat-error *ngIf="addvisitform.controls.dateOfDeath.errors?.required">DateOfDeath is required</mat-error>
```

## set validator and remove validator 

```
 isexipred():void {
    this.addvisitform.get('isExpired').valueChanges.pipe(takeUntil(this.onDestroy$)).subscribe((res) => {
      // console.log(res);
      if (res === 'true') {
        this.addvisitform.get('dateOfDeath').setValidators(Validators.required);
        this.addvisitform.get('preliminaryCauseOfDeath').setValidators(Validators.required);
        this.addvisitform.get('dateOfDeath').updateValueAndValidity();
        this.addvisitform.get('preliminaryCauseOfDeath').updateValueAndValidity();
      } else {
        this.addvisitform.get('dateOfDeath').removeValidators(Validators.required);||  we can use clear also if we want to clear every validator 
        this.addvisitform.get('preliminaryCauseOfDeath').removeValidators(Validators.required);
        this.addvisitform.get('dateOfDeath').updateValueAndValidity();
        this.addvisitform.get('preliminaryCauseOfDeath').updateValueAndValidity();
      }
    });
  }

```

###  validation if we does not need initialy so we can set it after that method is excecuted  and value changes 

```
  multipleBirthFlagvalueevent(){
   this.patientInfoForm.get('multipleBirthFlag').valueChanges.pipe(takeUntil(this.onDestroy$)).subscribe((res) => {
if (res == true) {
  this.patientInfoForm.get('multipleBirth').setValidators([Validators.required,Validators.min(1),Validators.max(10)]);
  
  this.patientInfoForm.get('multipleBirth').updateValueAndValidity();
} else {
  this.patientInfoForm.get('multipleBirth').clearAsyncValidators();
  this.patientInfoForm.get('multipleBirth').removeValidators([Validators.required,Validators.min(1),Validators.max(10)]);
  this.patientInfoForm.get('multipleBirth').updateValueAndValidity();
  this.patientInfoForm.get('multipleBirth').reset()

  
}
```
