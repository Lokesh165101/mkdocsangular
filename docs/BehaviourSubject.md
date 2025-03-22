
# Behaviour subject 

```
@Injectable({
  providedIn: 'root'
}) 

export class LocalDataSourceService {

first we need to creat the behaviour subject in the service class

 private vitalsUnitsStatus = new BehaviorSubject<any>(false);
  vitalsUnitsStatus$ = this.vitalsUnitsStatus.asObservable();
  
  
  here we need to creat a method storevitalsUnitsStatus in that same class 
  
  storevitalsUnitsStatus(value){
  this.vitalsUnitsStatus.next(value)
}

}

##app.ts 
where we need to set the data or send the data  

first we need to inject that servie 

private private datasource=inject(LocalDataSourceService), 

after that we need to set the data 
  this.datasource.storevitalsUnitsStatus(hideUnits);(here the data is present in the hideUnits )
  
  it call that method and behaviour subject is updated 
  
 ##child.ts (where we need to use it )
 
 first we need to inject that servie 

private private datasource=inject(LocalDataSourceService), 

again we need to subcribe that in that component and data will be in the res 


     this.localDataService.vitalsUnitsStatus$.pipe(takeUntil(this.onDestroy$)).subscribe(res=>{
      this.hideUnits=res;
    })
```