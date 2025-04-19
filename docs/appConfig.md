
# App Config.ts


```
import { DatePipe, HashLocationStrategy, LocationStrategy } from "@angular/common";
import { ApplicationConfig, importProvidersFrom } from "@angular/core";
import { provideRouter } from "@angular/router";
import { provideAnimationsAsync } from '@angular/platform-browser/animations/async';
import { routes } from "./app.routes";
import { provideHttpClient, withInterceptors } from "@angular/common/http";
import { MAT_MOMENT_DATE_ADAPTER_OPTIONS, MomentDateAdapter } from "@angular/material-moment-adapter";
import { DateAdapter, MAT_DATE_FORMATS, MAT_DATE_LOCALE, MatNativeDateModule } from "@angular/material/core";
import { jwtInterceptor } from "@core/interceptor/jwt.interceptor";
import { errorInterceptor } from "@core/interceptor/error.interceptor";
import { DateTimeAdapter, OWL_DATE_TIME_FORMATS, OWL_DATE_TIME_LOCALE } from "@danielmoncada/angular-datetime-picker";
import { MomentDateTimeAdapter } from "@danielmoncada/angular-datetime-picker-moment-adapter";
import { environment } from "@env/environment";
import { IConfig, provideEnvironmentNgxMask } from "ngx-mask";
import { NgxsModule } from "@ngxs/store";
import { BCState } from "@theme/breadCrum-store/breadcrum.state";
import { storeUserIdPhyIdState } from "./authentication/Store/auth.state";
import { storePatientIdState } from "./admin/patients/patient-store/patient.state";
import { storePatientIdVisitIdState } from "./er-dashboard/erdashboard-store/erdashboard.state";
import { storeMedicationState } from "./er-medications/er-medications-store/ermedications.state";
import { storeTemplatesState } from "./nurse-notes/store/template.state";
import { storeSchedulerState } from "./scheduler/scheduler-store/scheduler.state";
import { MnemonicState } from "./er-dashboard/erdashboard-store/mnemonic.state";
import { RoutingState } from "./er-dashboard/erdashboard-store/routing.state";
import { pageModuleMnemonicState } from "./home/store/pageModuleMnemonic.state";
import { masterDataState } from "./authentication/Store/master.state";
import { PatientRelatedStaffState } from "./er-dashboard/store/patient-related-staff.state";
import { StorePhysicianDataState } from "./home/store/physicians-store/physicians-data.state";
import { VitalsRangeState } from "./authentication/Store/vitalsRange.state";
import { storeNurStationidLocatioIdState } from "./authentication/Store/nursestationids.state";
import { ShiftTimingStateStore } from "./nurse-dashboard/nurse-dashboard-store/shiftTimingStore.state";
import { userDataState } from "./authentication/Store/allUsers.state";
import { NgxsStoragePluginModule } from "@ngxs/storage-plugin";
import { NgIdleKeepaliveModule } from "@ng-idle/keepalive";
import { NgxsResetPluginModule } from "ngxs-reset-plugin";
import { MAT_DIALOG_DATA, MatDialogRef } from "@angular/material/dialog";
import { MatDatepickerModule } from "@angular/material/datepicker";
import { TemplateState } from "./er-dashboard/erdashboard-store/template.state";
import { VitalState } from "./er-templates/store/vitals.state";
import { DashBoardDataState } from "./authentication/Store/erdashboard.state";
import { MnenusState } from "./er-dashboard/erdashboard-store/menus.state";
import { PatientBedDataState } from "./er-dashboard/erdashboard-store/patientBed.state";
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
    // fakeBackendProvider,
    //{ provide: APP_INITIALIZER, useFactory: appInitializer, deps: [UpdateCheckService], multi: true }
    //// present disabled after enable rabbitMQ in server
    /* {
        provide: RxStompService,
        useFactory: rxStompOutsideAngularServiceFactory,
        deps: [NgZone]
    },*/

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