# Interceptor

 Here we use 2 types of interceptor as per the consitions
 

# error interceptor
```
(where the golbal errors are writen here)
```

# jwt interceptor 
(here we will pass the tokens as per the condition)

```	
here the this interceptor should be mentioned in the app.config
    provideHttpClient(withInterceptors([jwtInterceptor])),
    provideHttpClient(withInterceptors([errorInterceptor])),
for more reference visit app.config page 	
```


## error interceptor
```
export const errorInterceptor: HttpInterceptorFn = (req, next) => {
  return next(req).pipe(catchError((error) => {
    if (
      (error.status === 401 || error.status === 403)
      && req.url.indexOf('/Login/') === -1
    ) {
      // console.log('renavigate.....',request.url)
      // auto logout if 401 response returned from api
      // this.authenticationService.logout();
      Swal.fire('', error.error, 'warning');
      // location.reload(true);
      logout();
    } else if (error.status === 500) {
      if (environment.production) {
        Swal.fire('', error.statusText, 'warning');
      } else {
       // Swal.fire('',  + error.error +'(' + error.status + '-' + error.statusText + ')'+ '\n(Service URL:' + error?.url + ')', 'warning');
      }
    }

    let errorMsg = null;
    if(error) {
      errorMsg = (error.message ? error?.error?.error+''+ error.message: error.error.message)  || error.statusText;
    }

    return throwError(() => errorMsg);
  }));
}
```

# jwt interceptor
```

export const jwtInterceptor: HttpInterceptorFn = (req, next) => {

  const authService = inject(AuthService);

  // add authorization header with jwt token if available
  if (req.url.startsWith(environment.imageBaseUrl)) { // For Image base URL services.
    let imageToken: string = localStorage.getItem('imageToken');
    if (imageToken) {
      req = req.clone({
        setHeaders: {
          Authorization: `Bearer ${imageToken}`,
        }
      });
    }
  } else if (req.url.startsWith(environment.aiBaseURL)) { // For Image base URL services.
    let aiToken: string = localStorage.getItem('aiToken');
    if (aiToken) {
      req = req.clone({
        setHeaders: {
          Authorization: `Bearer ${aiToken}`,
        }
      });
    }
  }else if (req.url.startsWith(environment.openAI)) { // For open AIe URL services.
    let aiToken: string = environment.aiToken;
    if (aiToken) {
      req = req.clone({
        setHeaders: {
          Authorization: `Bearer ${aiToken}`,
        }
      });
    }
  }else { // For falcon api services.
    let currentUser = authService.currentUserValue;
    if (currentUser && currentUser.token) {
      req = req.clone({
        setHeaders: {
          Authorization: `Bearer ${currentUser.token}`,
        },
      });
    }
  }

  return next(req);
};
```

# basic interceptor 

```
authinterceptor.ts

import { Injectable } from '@angular/core';
import { HttpInterceptor, HttpRequest, HttpHandler, HttpEvent } from '@angular/common/http';
import { Observable } from 'rxjs';

@Injectable()
export class AuthInterceptor implements HttpInterceptor {
  
  intercept(req: HttpRequest<any>, next: HttpHandler): Observable<HttpEvent<any>> {
    console.log('Intercepted HTTP request:', req);

    // Modify the request (e.g., add Authorization header)
    const clonedReq = req.clone({
      setHeaders: {
        Authorization: `Bearer ${localStorage.getItem('token')}`
      }
    });

    // Pass the modified request to the next handler
    return next.handle(clonedReq);
  }
}
```

# we need to provide them in the appconfig.ts 
```
import { HTTP_INTERCEPTORS } from '@angular/common/http';
import { AuthInterceptor } from './interceptors/auth.interceptor';

@NgModule({
  providers: [
    { provide: HTTP_INTERCEPTORS, useClass: AuthInterceptor, multi: true }
  ]
})
export class AppModule { }
``` 





