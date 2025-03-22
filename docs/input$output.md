input decorator (parent to child relationship )



```

Input decorator and ngonchnges

@input parent to child 

parent ts 
i am having a data in the parent component i want send to the child 

array=[1,2,3,4] this is oresent in the parent component 

or

formsubmitbutton(){
this.array=[...this.array,this.form.value](here we are pushing the formdata to that array)  
}

parent html --

<app-child [array]="array"></app-child>(the selector of the child componenet )

chid ts -

@Input array:any( here the data comes in that array from the paremt )

we can use it in any way 

child html 
<p>child works!</p>
@for(item of array ;track item ){  (track is used for the performance)
  
  <li>{{item.firstname}}</li>
}
@empty{ (if the data is not present )
  <li>there is no data </li>
}


why we need to use ngOnChanges

- the data is send from parent to child intitally when the component is loded 
only the initial data will come 

but when we need updated data of that array when the form is submitted 
so the updated data is triggered in that ngOnchnages


ngOnChanges(changes: SimpleChanges): void {
  // Object.keys(changes).forEach(key => this[key] = changes[key].currentValue);

if(changes['array']?.currentValue){
  let obj = changes['array']?.currentValue
  console.log(obj,'datadata')

}


}


```




parent compnent 

```
  parent compnent 
    getNameTypeCode() {
    this.masterDataService.getNameCodes().pipe(takeUntil(this.onDestroy$)).subscribe(res => {
      this.name_type_code = res.body;
      this.nameTypeCodeStatus = true;
      ////console.log.log.log("name type code ==> ", res.body);
    })
    },
```

i need to sen this data name_type_code to raming componets 

1)  declear this   name_type_code: NameTypeCodes[]; in top after the export classs we need to declear there 

2) in parent html 
  [name_type_code]="name_type_code" we need to write like this inside child selector

child component

3) child component 

@Input() name_type_code: NameTypeCodes[]; here the data is we will get 

we can directly use this in the html.  

here the data is present in that name_type_code so we can use there we need 

```
  https://stackblitz.com/edit/angular-input-decorator-test?file=src%2Fapp%2FchildComponent%2Fchild.component.ts,src%2Fapp%2Fapp.component.html,src%2Fapp%2Fapp.component.ts -- link ( for reference)

```
another example

```
CHILD HTML 
<h4> from child : ==>

{{dropdownItems}} we are not having this data in this html or ts 
</h4>
CHILD TS 
export class ChildComponent implements OnInit {

@Input() dropdownItems: any[]; --- dropdownitems is an array it is not present here 

export class AppComponent  {
distanceDropdownItems: any[];
name = 'testing';
constructor() { }

ngOnInit() {
this.distanceDropdownItems = ['hello', 'you', 'there'];
}
  
APP HTML 
  

<app-child [dropdownItems] = "distanceDropdownItems"></app-child>
  
[dropdownItems]----- THIS IS USED AS INPUT IN THE CHILD TS 
distanceDropdownItems------ THIS HAS THE ARRAY DATA 

```


### output decorater 
(child to parent) 

 
```
CHILD HTML

<input type="text" #price (keyup)="onChange(price.value)"/>

CHILD TS 

export class ChildComponent implements OnInit {

  constructor() { }

  @Output() public newPrice = new EventEmitter<any>();

  public price:any;

  ngOnInit() {
  
  }

   onChange(value) {
    this.newPrice.emit(value);
  }

}

PARENT HTML 

<h1>
  Parent component
</h1>
<h4>Current Price : {{price}}</h4>
<app-child (newPrice)="onchange($event)"></app-child>

(newPrice) lo data untade so we are transfaring the data 
onchnage($event)== event loki data vasthade 

PARENT TS 

export class ParentComponent implements OnInit {

  constructor() { }

  ngOnInit() {
  }

  public price:any;
  onchange(value){
      this.price = value;
  }

}
```