
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

```js
// filepath
var filePathRegex = /(?:[^\/\\]*[\/\\]){2}(?:[^.]*[.]){1}/gm;
Boolean(tests[test].match(filePathRegex))
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

## JWT
* A JWT is easy to identify. It is three strings separated by period (. the dot) symbol. Ex: `a0.b1.c9`
* They are: `header`, `payload`, `signature`
* The canActivate method returns a boolean indicating whether or not navigation to a route should be allowed. If the user isn’t authenticated, they are re-routed to some other place, in this case a route called /login.
* JWT CAN NOT be validated in Front-End. You could check if it has expired.
You can break down the JWT Token at JWT.io's debugger tool.
* SECRET: the secret used to sign the jwt token (default `secret`)
* [link] (https://gist.github.com/hamzeen/824761ffe3c605fa3c7ee270d871dc51)

## Signing or Creating A JWT
```js
const jwt = require('jsonwebtoken');
// Create a token
const payload = { user: user.name };
const options = { expiresIn: '2d', issuer: 'https://scotch.io' };
const secret = process.env.JWT_SECRET;
const token = jwt.sign(payload, secret, options);
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

```js
// countries class
import { countryCodes } from '../constants/countryCodes';
export class Util {
  public countries: any[];

  public getProducts() {
    for(var i in countryCodes)
      this.countries.push([i, countryCodes[i]]);

    return this.countries;
  }
}

import { countries } from ‘../constants/countryCodes’;
import { Util } from ‘./util’;
 
let testClass: Util = null;
describe(‘Util Tests', () => {
  beforeEach(() => {
    testClass = new Util();
  });
 
  it('should ensure getCountries is based on countries file', () => {
    const actual = testClass.getCountries;
    expect(actual[0].id).toEqual(countries[0].id);
  });
});

// constants/countryCodes.ts
export const countries = {
  'AF': 'Afghanistan',
  'SG': 'Singapore'
}
```
