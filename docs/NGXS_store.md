
## NGXS store 


# let us assume we are having data that we need to store in the angular appplication so we use store

```
loginmessgedirectid.actions.ts
export class DirectMessageLoginId {
  static readonly type = '[DirectMessageLoginId] DirectMessageLoginId';(this line is optional)

  constructor(public payload: any) {
  }
  
```
# from here we nned to creat the state.ts 

```
loginmessgedirectid.State.ts
  
  import { State, Action, StateContext, Selector } from '@ngxs/store';
import { Injectable } from '@angular/core';
import { DirectMessageLoginId } from './directMessagesLoginId.action';


const defaultState = {
  mailId: null
} (it will take defalut values intinally )

@State<any>({
  name: 'DirectMessageLoginId',
  defaults: defaultState
})
@Injectable()

export class DirectMessageLoginIdState {

  mailId: number

  @Action(DirectMessageLoginId)
  ErDashBoardData({ getState, patchState }: StateContext<any>, { payload }: any) {


    const state = getState();

    patchState({
      mailId: payload.mailId
    });


  }

}

}
```
### we need to import this store in app.configs.ts

```
import { DirectMessageLoginIdState } from "./authentication/Store/directMessagesLoginId.state";
const maskConfig: Partial<IConfig> = {
  validation: false,
};

export const appConfig: ApplicationConfig = {
  providers: [ 
    {
      provide: LocationStrategy,
      useClass: HashLocationStrategy
    },
    provideRouter(routes),
    provideAnimationsAsync(),
    provideHttpClient(),
    provideHttpClient(withInterceptors([jwtInterceptor])),
    provideHttpClient(withInterceptors([errorInterceptor])),
    {
      provide: MAT_MOMENT_DATE_ADAPTER_OPTIONS,
      useValue: { useUtc: false }
    },


    { provide: MatDialogRef, useValue: {} },
    { provide: MAT_DIALOG_DATA, useValue: {} },
    DatePipe,


    {
      provide: DateAdapter,
      useClass: MomentDateAdapter,
      deps: [MAT_DATE_LOCALE, MAT_MOMENT_DATE_ADAPTER_OPTIONS]
    },
    { provide: MAT_DATE_FORMATS, useValue: environment.MY_DATE_FORMATS },
    { provide: DateTimeAdapter, useClass: MomentDateTimeAdapter, deps: [OWL_DATE_TIME_LOCALE] },
    { provide: OWL_DATE_TIME_FORMATS, useValue: environment.MY_OWL_FORMATS },
    provideEnvironmentNgxMask(maskConfig),

    importProvidersFrom(
      NgxsModule.forRoot([
        BCState,
        storeUserIdPhyIdState,
        storePatientIdState,
        storePatientIdVisitIdState,
        storeMedicationState,
        storeTemplatesState,
        storeSchedulerState,
        MnemonicState,
        RoutingState,
        pageModuleMnemonicState,
        masterDataState,
        PatientRelatedStaffState,
        StorePhysicianDataState,
        VitalsRangeState,
        storeNurStationidLocatioIdState,
        ShiftTimingStateStore,
        userDataState,TemplateState,VitalState,
        DashBoardDataState,MnenusState, PatientBedDataState,DirectMessageLoginIdState
      ], { developmentMode: !environment.production }),
      NgxsStoragePluginModule.forRoot(),
      NgIdleKeepaliveModule.forRoot(),
      NgxsResetPluginModule.forRoot(),
      MatDatepickerModule,
      MatNativeDateModule
    )
  ]
};
```

## data where we need to send to the store 

```
this.store.dispatch(new DirectMessageLoginId(data));
```

## Subscribe to Store using select()

```
  @Select(DirectMessageLoginIdState) mailId$: Observable<any>;

  constructor(private store: Store) {}

  ngOnInit() {
    // Subscribe to mailId$ to get updates
    this.mailId$.subscribe(value => {
      console.log('Mail ID from store:', value);
    });
  }
```
