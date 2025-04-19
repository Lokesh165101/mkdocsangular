# Angular Component Structure


```
import { ChangeDetectionStrategy, ChangeDetectorRef, Component, inject, OnDestroy, OnInit } from '@angular/core';


@Component({
  selector: 'app-radiology-view',
  standalone: true,
  changeDetection: ChangeDetectionStrategy.OnPush, --- changeDetection
  imports: [NgIf, CommonModule, NgFor],
  templateUrl: './radiology-view.component.html',
  styleUrl: './radiology-view.component.scss'
})




export class CompoenntStructure {
 private _changeDetectorRef = inject(ChangeDetectorRef);

```
# change detection
```
  onChangeDetectMarkForCheck(): void {
    this._changeDetectorRef.markForCheck();
  }
```

# ngondestroy

```
   ngOnDestroy(): void {
    this.onDestroy$.next(false);
    this.onDestroy$.unsubscribe();
  }

```

# Service with rxjs 

```
this._radiologyService.getLabResultImage(4,5).pipe(takeUntil(this.onDestroy$)).subscribe({
  next:(res)=>{

  },
  error:(err)=>{
    
  }

```
# Normal service 

```
private http = inject(HttpClient)

this.http.post('service'postdata).subcribe({
  next:(res)=>{

  },
  error:(err)=>{
    
  }
})

in mains.ts or appconfig.ts
import { HttpClientModule, provideHttpClient } from '@angular/common/http';

bootstrapApplication(AppComponent, {
  providers: [provideHttpClient()]  // ✅ Provide HttpClient in a standalone app
});

}


```