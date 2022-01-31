
# Angular

## NG CLI - Generate
* `npx ng genearate component currency-converter --force`
* `npx ng genearate service history --force`

* Code scaffolding:ng generate component component-name to generate a new component. 
* You can also use ng generate directive|pipe|service|class|guard|interface|enum|module.

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
