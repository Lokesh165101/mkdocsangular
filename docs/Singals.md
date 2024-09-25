```
	-----SIGNALS ----- COMPOUND COMMUNICATION 
	
		1) in the services folder we need to creat a signals or set a signal there
	  
	  export class ImplantSignal {
       udiList = signal([]);-- in the form of array 
       setUdiList(udiList: string[]): void {
         this.udiList.set(udiList);---- set the data 
      }
       list = signal(null);
       setpatientlist(list: any): void {
       this.list.set(list);
    }



    	2)  private _implantSignal = inject(ImplantSignal);---- we nedd to inject it in the class 
	  this._implantSignal.setpatientlist(patientObj);--- the data is prsent in that patientobj


       let udiList: string[] = implants.map(obj => obj.udi);//extra code
      this._implantSignal.setUdiList(udiList);


  3)    the componet where we need to use and set the data 
  we need to inject it in the class ---(private _implantSignal = inject(ImplantSignal);) 
	      effect(() => { -- import from angular/core 
      this.udiList = this._implantSignal.udiList();
```
