```js
function isObject(obj: any): boolean {
    return (typeof obj === "object" || typeof obj === "function") && obj !== null;
}

/**
 * This function can be used to lookup value
 * of certain property at any depth in an object
 * @param: record
 * @param: propertyName
 * @param: valueToMatch 
 */
const isProductOf = (record: Insurance, propertyName: string, valueToMatch: string): boolean => {
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
