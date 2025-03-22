# ng-container 


## without using ng-container

```
<ul>
  <div *ngFor="let item of items">
    <li>{{ item }}</li>
  </div>
</ul>

items=[1,2,3,4,5]


output 
<div> 1 </div>
<div> 2 </div>
<div> 3 </div>
<div> 4 </div>
<div> 5 </div>
```
here we can see that in that output all the divs are coming when we inspect the code 

## when we use ng-container

```
<ul>
  <ng-container *ngFor="let item of items">
    {{ item }}
  </ng-container>
</ul>

output 
 1 
 2
 3 
```
here we cna see that in that ouput only the values will appear when we inspect the code the extra div is not appear 


 
# ng contant 

Here the ng contant is used parent and child communicaton 

when we insert the data in the selector from parent  it is going the show the same data in the child 
```<ngcontent> here the data is going to show  </ngcontent>```

```
parent html
<app-child>
here is the data 
</app-child>

child

<div> hello this is the child html </div>
<ng-conant> 
(here the data will come from the parent a display here )
</ng-conant
```

here the any data given in the selector that will be diplsayed in the ng-contant in the child 


# NG-TEMPLATE  

## where we need to use ng -templte with structural directive 
 
```
<div *ngIf="login;else temp">
 login sucess
 </div>
 
 tsfile 
 login=true
 
 <ng-template #temp>
 <div> display only  when temp is false </div>
 </ng-template>
```

