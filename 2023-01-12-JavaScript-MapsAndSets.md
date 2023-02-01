# JavaScript: Maps and sets

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
console.log("Second value", secondValue);
```

### Map contents with the entries method

- Returns an iterator object that contains the key-value pairs for each element
  ```js
  //What is the third set of entries in your saturday Map object?
  const saturdayEntries = saturday.entries();
  saturdayEntries.next();
  saturdayEntries.next();
  const thirdEntry = saturdayEntries.next().value;
  console.log("The third entry in my saturday Map object is: ", thirdEntry);
  //Returns an array with thr third Object
  //The third entry in my saturday Map object is:  [ 3, 'watch a movie' ]
  ```

### Loop over a map with forEach

- Executes a provided cacllback function for each key-value pair in the Map object
- 4 Optional parameters
  - value
  - key
  - map
  - thisArg
  ```js
  //Using the forEach method, if a key is equal to 12,
  //console log the value of the key.
  saturday.forEach((value, key) => {
    if (key === 12) {
      console.log(`It's time for ${value}`);
    }
  });
  ```

---

## 2. WeakMaps

### What is the WeakMap Object?

- The difference is that keys are weak and can be garbage collected (A way of freeing up memory thta has been allocated to objects that are no longer in use)
- the process of garbage collection is performed automatically in JS

- How they are the same

  - Both contain key-value pairs
  - Both allow you to set, get, delete, and check for key-value pairs

- Key differences

  - WeakMap's keys must be objects
  - WeakMap does not have all of the same methods and property as Map, including the ability to iterate over the object or get its size
  - Methods available in WeakMap
    - set
    - get
    - has
    - delete

- Constructor

  ```js
  const myFisrtWeakMap = new WeakMap();
  ```

- Description taken from [stackoverflow](https://stackoverflow.com/questions/29413222/what-are-the-actual-uses-of-es6-weakmap#:~:text=WeakMaps%20provide%20a%20way%20to,a%20WeakMap%20can%20be%20applied.)
  - WeakMaps provide a way to extend objects from the outside without interfering with garbage collection. Whenever you want to extend an object but can't because it is sealed - or from an external source - a WeakMap can be applied.
  - A WeakMap is a map (dictionary) where the keys are weak - that is, if all references to the key are lost and there are no more references to the value - the value can be garbage collected.

---

## Sets

### The Set Object Defined

- Collection of unique values
- No duplicates
- Set values can be anything
- Several Methods (add, has, clear, delete, entries, forEach, values)
- Size property

  ```js
  const myFirstSet = new Set();
  ```

### Add values to your set

- Can chain add methods

  ```js
  const iceCream = new Set();
  iceCream
    .add("chocolate")
    .add("vanilla")
    .add("coffee")
    .add("coffee")
    .add("strawberry")
    .add("vanilla");

  console.log("Ice Cream Flavor List", iceCream);
  //Result: Ice Cream Flavor List Set(4) { 'chocolate', 'vanilla', 'coffee', 'strawberry' }
  ```

### Does set have your value?

- Returns true or false depending on wheter or not a value is contained in a Set object

```js
const hasMintChocChip = iceCream.has("mint chocolate chip");
console.log("Does the Set contain Mint Chocolate Chip? ", hasMintChocChip);
//Result: Does the Set contain Mint Chocolate Chip?  false
```

### Get your set size

- a property, not a method

  ```js
  console.log(`Our Set is ${iceCream.size} in size.`);
  ```

### Delete and clear values in your set

```js
//Delete vanilla from the iceCream Set.
iceCream.delete("vanilla");
console.log("iceCream Set after removing vanilla", iceCream);

//Clear the iceCream Set.
iceCream.clear();
console.log("Checking Set size after clearing ", iceCream.size);
```

### iterate over values in a set

- just like the values method on map, the values method for set also returns an integrator object.

  ```js
  const values = setObject.values();
  const firstValue = values.next().value;
  ``` 

- the example
  ```js
  const iceCreamValues = iceCream.values();
  iceCreamValues.next();

  const secondValue = iceCreamValues.next().value;
  console.log(“The second value in my Set is: “, secondValue);
  ```

### iterate over a set with entries

- returns an integrator object that contains an array [array, array] in insertion order. Since set only has values, different than maps.
 
- twice in order to keep the API similar to map.

  ```js
  const entries = setObject.entries();
  const firstEntries = entries.next().value;
  ``` 

- the example

  ```js
  const iceCreamEntries = iceCream.entries();
  const firstEntry = iceCreamEntries.next().value;
  console.log(“The first entry in my iceCream Set is: “, firstEntry)
  ```

### iterate over your set with forEach

- executed a provided callback function for each value in the Set object

  ```js
  //Loop through our iceCream Set and if the value does NOT equal ‘vanilla’,
  //log it in the console.
  iceCream.forEach((flavor) => {
      if(flavor !== ‘vanilla’) {
          console.log(“Non-vanilla flavor: “, flavor)
      }
  });
  ```

---

## Weaksets

### what is?

- the weakest can be garbage collected if there is no other reference to it
- how they are the same
  - both store unique values
  - bot allow you to add, delete, and check values
- key differences
  - weakset’s values must be objects
  - weaksets only have add, has and delete methods


### same methods. Different set

- add
- has
- delete
 