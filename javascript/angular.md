
# Angular

## NG CLI - Generate
* `npx ng genearate component currency-converter --force`
* `npx ng genearate service history --force`

* Code scaffolding:ng generate component component-name to generate a new component. 
* You can also use ng generate `directive`|`pipe`|`service`|`class`|`guard`|`interface`|`enum`|`module`.
* package.json: "network": "ng serve --host 0.0.0.0"


## RegEx

```js
// 2 times the same character consecutively
static valdiateUsername(control: AbstractControl): { [key: string]: boolean } | null {
    const regex = new RegExp("([a-zA-Z\\d])\\1");
    if(!control.value || (control.value && !Boolean(control.value.match(regex)))) {
      return { invalidUsername: true }
    }
    return null;
}
```

## Adding controls after defining group:
```js
constructor(private fb: FormBuilder) {
    this.myForm = fb.group({
        'name': ['', [Validators.required],
        'surname': ['', [Validators.required],
        'email': ['', [validateEmail]],
    });
}
this.myForm.addControl('newcontrol',[]);
```

## Directives
Classes that additional functionality to elements.

## angular.js vs angular
Angular is based on TypeScript while AngularJS is based on JavaScript.  
TypeScript is a superset of ES6 and it's backward compatible with ES5.  
Angular has also benefits of ES6 like: lambda operators, iterators or reflection's mechanism.

## Service
```javascript
import { Injectable } from '@angular/core';
import { HttpClient } from '@angular/common/http';
import {Grocery} from '../interfaces/grocery';


@Injectable({
  providedIn: 'root',
})
export class AppStateService {
  private groceryDetail: Grocery;

  constructor(private http: HttpClient) {
  }

  getGroceryDetail() {
    return this.groceryDetail;
  }
  setGroceryDetail(userSelection: Grocery) {
    this.groceryDetail = userSelection;
  }
}

```

## local storage
```js
localStorage.setItem('abc','a')
localStorage.getItem('abc')
```


# Unit Testing

## Basic
```js
// app.component.spec.ts
import { TestBed, async } from '@angular/core/testing';
import { AppComponent } from './app.component';

describe('AppComponent', () => {

  let component: AppComponent;
  let fixture: ComponentFixture<AppComponent>;

  beforeEach(async(() => {
    TestBed.configureTestingModule({
      declarations: [ AppComponent ]
    })
    .compileComponents();
  }));

  beforeEach(() => {
    fixture = TestBed.createComponent(AppComponent);
    component = fixture.componentInstance;
    fixture.detectChanges();
  });

  it('should create the component', () => {
    expect(component).toBeTruthy();
  });
}
```
