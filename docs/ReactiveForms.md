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
  })

```