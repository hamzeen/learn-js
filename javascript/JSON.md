## find given value for a given prop at any depth of `an Object`
```js
const sales = [
  {
    product: "TravelBag”,
    travelBagInformation: {
      price: 3,
      user: "Joe"
    }
  }, {
    product: “Model”Car,
    carInformation: {
      lights: true,
      user: "Joe"
    }
  }, {
    product: “LegoHome",
    modelInformation: {
      price: 5,
      user: “Nick”
    }
  }
];

function isObject(obj) {
    return (typeof obj === "object" || typeof obj === "function") && obj !== null;
}

/**
 * This function can be used to lookup value
 * of certain property at any depth in an object
 * @param: record
 * @param: propertyName
 * @param: valueToMatch 
 */
const isProductOf = (record, propertyName, valueToMatch) => {
    if (!isObject(record)) {
        return false;
    }

    for (var key in record) {
        if (typeof record[key] === "object") {
            return isProductOf(record[key], propertyName, valueToMatch);
        } else {
            if (key === propertyName && record[key] === valueToMatch) {
                return true;
            }
        }
    }
    return false;
};
```

## FLATTEN: after pushing parent node into children
```js
const groups = [
  {
     "id": "+91611111111", 
     "seats":[{
       "section":"main hall",
       "row":"1",
       "seat":"4"
     }, {
       "section":"main hall",
       "row":"1",
       "seat":"3"
     }] 
  },
  {
     "id": "+91611111112", 
     "seats":[{
           "section":"balcony",
           "row":"1",
           "seat":"1"
       }, {
           "section":"balcony",
           "row":"1",
           "seat":"2"
       }]
  }];
  
// M1: moves parant prop to children & flattens it.
const flatGroups = groups.map((item, idx) => {
        return item['seats'].map((seat) => {
            return {...seat, label: `L${idx+1}`, id: item['id']};
        });
    }).flat();
    
    

// M2: without using spread operator
const flatGroups = groups.map((item, idx) => {
        return item['seats'].map((seat) => {
            seat.label = `L${idx+1}`;
            seat.id = item['id'];
            return seat;
        });
    })
    .flat();



// M3: copies parent prop to children
const flatGroups = groups.map((item, idx) => {
        item['seats'].map((seat) => {
            seat.label = `L${idx+1}`;
            seat.id = item['id'];
            return seat;
        });
        return item;
    });
    
// M3: get a flat array
const flatAry = [].concat(...flatGroups.map((ap) => ap['seats']));
```
