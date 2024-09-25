
```
   FORK JOINT
   fork joint---(let services = [this.postVisitObs(addvisit)];
        if (this.addvisitform.value.isExpired==true) {
          services.push(this.postvisitIsexpired(isExpireddata));
        }
        forkJoin([
          // this.postVisitObs(addvisit),
          // this.postvisitIsexpired(isExpireddata)
          ...services
        ]).pipe(takeUntil(this.onDestroy$)).subscribe(res => {
          this.isUpdateVisit = false;
          this.isSubmitted = false;
          if (res[0].body.value == existVisitErrMsg) {
            Swal.fire(res[0].body.value);
          } else {
            this.snakbar.open(' Patient Information Saved  Successfully', 'OK', {
              duration: 2000,
            });-----------------------------------
			
			
			  ngOnDestroy(): void {
    this.onDestroy$.next(false);
    this.onDestroy$.unsubscribe();
  }

```