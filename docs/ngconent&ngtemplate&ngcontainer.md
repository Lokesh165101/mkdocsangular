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

here ngcontenet 

```
<app-child>ll;lk;lk;k;</app-child>
```

the data is wrote in the app.html  i want to show the dat in the child html view 

so in that child.html
```
<p>child works!</p>
<ng-content></ng-content>
```

Here i wrote that data in the parent html in the child  slector  the data will show in the child 


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

