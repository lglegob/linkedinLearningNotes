# JavaScript: Maps and setuptest

- Jamie Pittman

## Maps

### the Map object defined

- Recently introduced
- Similar to Objects, both contain key-value pairs
- both allow you to set, get, delete, and check for key-value pairs
- Maps does not contain default keys: they must be set
- Maps keys can be anything
- Maps size property (number of items)
- Maps does not allow duplicate values in keys

```js
const myFirstMap = new Map();
```

### Build your Map object with the set method

- the set method is what you will use to creatre key value pairs in your map

  ```js
  const saturday = new Map();

  saturday.set(8, "walk the dogs");
  saturday.set(12, "lunch");
  saturday.set(3, "watch a movie");
  ```

### Access a value with get

- if the key exists, associated value is returned. if the key does not exist, undefined is returned.

  ```js
  const noon = saturday.get(12);
  ```

### Does the map have your key?

- Returns true or false based on whether the value of the provided key exists

  ```js
  const hasFour = saturday.has(4);
  ```

### Determine map size

- The number of elements, or key-value pairs, contained in Map()
- because it is a property, without parenthesis

  ```js
  const saturdaySize = saturday.size;
  ```

### Remove key-value pairs with clear and delete

- Delete Method removes a key-value pair from an existing Map Object
- Returns True if the key-value pairs was successfully deleted
- Returns False if it did not exist in the Map()

```js

```

- Clear Method removes all elements from a Map Object

```js
//Delete the element associated with the key 10.
console.log("Did the key 10 get deleted?", saturday.delete(10));
//Clear the entire saturday Map object.
saturday.clear();
```

### Map: Keys and values methods

- iterator: An object which defined a sequence and potentially returns a value upon its termination.
- with our Map, some of its methods return iterators which allow us to cycle through keys and values
- keys method
  - returns an iterator object with the keys in their insertion order.
- values method
  - returns an iterator object with the values in their insertion order.
- these methods ussually are aplied by creating a const with the method, and then another conts using the next method to get the key or value desired.
```js
//What is the first key in your saturday Map object?
const saturdayKeys = saturday.keys();
const firstKey = saturdayKeys.next().value;
console.log("First key", firstKey);

//What is the second value in your saturday Map object?
const saturdayValues = saturday.values();
saturdayValues.next();
const secondValue = saturdayValues.next().value;
console.log("Second value", secondValue)
```

