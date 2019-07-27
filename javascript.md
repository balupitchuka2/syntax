1. [ Array Operations Cheat Sheet. ](#aocs)










 
 <a name="aocs"></a>
 ## Array Operations Cheat Sheet
  An array is a list-like object with extensive use cases. The most common, in my opinion, are described in this cheat sheet.

#### Create a new array

```
let cars = ['Mazda', 'Ford', 'BMW'];
// or
let cars = new Array('Mazda', 'Ford', 'BMW');

console.log(cars); // outputs ['Mazda', 'Ford', 'BMW']
```

#### Item access

```
let car = cars[1];
console.log(car); // outputs 'Ford'

    Items are accessed via index. Indexing starts at 0
```

##### Add new item at the end of an array
```
let newLength = cars.push('Opel');
console.log(cars); // outputs ['Mazda', 'Ford', 'BMW', 'Opel']

    Method push returns the new length of an array. In our example, it will return the number 4
```
#### Add new item at the beginning of an array
```
let newLength = cars.unshift('Renault');
console.log(cars); // outputs ['Renault', 'Mazda', 'Ford', 'BMW', 'Opel']

    Method unshift returns the new length of an array. In our example, it will return the number 5
```
#### Remove an item from the end of an array
```
let removedItem = cars.pop();
console.log(cars); // outputs ['Renault', 'Mazda', 'Ford', 'BMW']

    Method pop returns the removed item. In our example, it will return the text 'Opel'
```
#### Remove an item from the front of an array
```
let removedItem = cars.shift();
console.log(cars); // outputs ['Mazda', 'Ford', 'BMW']

    Method shift returns the removed item. In our example, it will return the text 'Renault'
```
#### Remove an item from the specific position
```
let removedItem = cars.splice(2, 1);
console.log(cars); // outputs ['Mazda', 'Ford']

    Method splice returns the removed items. In our example, it will return an array with one item ["BMW"]
```
#### Add an item at the specific position
```
let removedItem = cars.splice(1, 0, 'BMW');
console.log(cars); // outputs ['Mazda', 'BMW' 'Ford']

    The code above will insert a new item (BMW) at the position 1. The second parameter is the number of items we want to delete. After calling splice, the returned array will be empty because we didn't delete anything (0 was provided as the second parameter)
```
#### Replace an item at the specific position
```
let removedItem = cars.splice(2, 1, 'Renault');
console.log(cars); // outputs ['Mazda', 'BMW', 'Renault']

    The method splice, in this case, will return an array with one item ['Ford']
```
#### Reverse an array
```
let carsRev = cars.reverse();
console.log(cars); // outputs ['Renault', 'BMW', 'Mazda']

    NOTE: reverse method WILL MODIFY the original array
```
#### Sorting
```
The method sort sorts the elements of an array and returns the sorted one.

let cities = ['Paris', 'London', 'New York', 'Barcelona', 'Madrid', 'San Francisco'];
cities.sort();
console.log(cities); // outputs ['Barcelona', 'London', 'Madrid', 'New York', 'Paris', 'San Francisco']

// custom sorting function - sorts our array by name length in ascending order
cities.sort((cityA, cityB) => {
   // if the result is less than 0 cityA comes first
   // if the result is greater than 0 cityB comes first
   // if the result is equal to 0 the items remain unchanged concerning each other
   return cityA.length - cityB.length;
});

console.log(cities); // outputs ['Paris', 'London', 'Madrid', 'New York', 'Barcelona', 'San Francisco']

    NOTE: sort method WILL MODIFY the original array
```
#### Filtering
```
Array filter method returns a new array filled with items that passed the provided condition in the callback. If no elements pass the condition, an empty array is returned.

// example 1
let citiesByLength = cities.filter(city => {
    return city.length > 6;
});
console.log(citiesByLength) // outputs ['New York', 'Barcelona', 'San Francisco']

// example 2
let citiesWithTwoWords = cities.filter(city => {
    let words = city.split(' '); // split by an empty space;
    return words.length > 1;
});

console.log(citiesWithTwoWords); // outputs ['New York', 'San Francisco'];

    NOTE: filter method DOES NOT modify the original array
```
#### Find the specific item or its index
```
Methods find and findIndex return the value of the first occurrence within an array that satisfies the condition

// find an item
let city = cities.find(city => {
    return city === 'London';
});
console.log(city); // outputs 'London'

// find an index
let cityIndex = cities.findIndex(city => {
    return city === 'London';
});
console.log(cityIndex); // outputs 1

    NOTE: method find stops the loop after the first item is found, meaning that if we had two cities with the name London only the first one would be returned. Method findIndex works the same way, but the difference is that it returns an item index. They WILL NOT modify the original array
```
#### Loops
```
Method forEach executes the provided callback for each item within an array

cities.forEach(city => {
    console.log('Current iteration item: ' + city);
});

// outputs:
// 'Current iteration item: Paris' 
// 'Current iteration item: London'
// 'Current iteration item: New York'
// 'Current iteration item: Barcelona'
// ...
```
#### Mapping
```
The method map creates a new array based on the result of the provided callback

let capitalizedCities = cities.map(city => {
    return city.toUpperCase();
});
console.log(capitalizedCities); // outputs ['PARIS', 'LONDON', 'NEW YORK', 'BARCELONA', 'MADRID', 'SAN FRANCISCO']
```
#### Type Check (is an array)
```
Good to know is that method isArray will return false for a falsy value, therefore we don't need to check manually if the value is defined or not, for example. Maybe this method is not that commonly used, but I felt like it should be in this cheat sheet due to the old way of doing things.

// without isArray
console.log(Object.prototype.toString.call(cities) === '[object Array]'); // outputs true

// with isArray
console.log(Array.isArray(cities)); // outputs true
console.log(Array.isArray(undefined)); // outputs false
console.log(Array.isArray(null)); // outputs false
console.log(Array.isArray('Hello')); // outputs false
```
#### Conversion
```
The method from creates a new array by shallow-copying the array-like object given as a source. A common use case is a situation where we need to extract unique values from the source and place the result in an array. Combining Array.from with a Set we can achieve that, but do note that it works with primitive values only.

console.log(Array.from('Hello World')); // outputs ['H', 'e', 'l', 'l', 'o', ' ', 'W', 'o', 'r', 'l', 'd']

// example 2
let fruits = ['Apple', 'Banana', 'Grape', 'Apple', 'Watermelon'];
console.log(Array.from(new Set(fruits))); // outputs ['Apple', 'Banana', 'Grape', 'Watermelon']
```
#### Item existence
```
To check if an array contains a specific element, we can use a new method called includes. A use case for this would be replacing an if statement containing multiple || operators.

// without includes
if(model === 'renault' || model === 'peugeot') { // more conditions
  console.log('model valid');
}

// with includes
let models = ['peugeot', 'renault'];

if(models.includes(model)) { 
  console.log('model valid');
}

    I've written an entire article related to JavaScript conditionals. Read about it here Tips and Tricks for Better JavaScript Conditionals and Match Criteria
```
#### Validating any
```
By invoking the method some we can check if at least one of the items within an array passes the given condition. It will invoke the given callback for each item in the array and will return true immediately if a truthy item is found.

const cars = ['Mazda', 'Ford', 'BMW', 'Mercedes'];
const startsWithLetterM = (item) => {
  return item.charAt(0).toLowerCase() === 'm';
}
console.log(cars.some(startsWithLetterM)); // outputs true
```
#### Validating all
```
The method every validates if all items within an array pass the given condition. It will invoke the callback for each item in the array and will return false immediately if a falsy item is found.

console.log(cars.every(startsWithLetterM)); // outputs false
```
#### Reducing
```
In my opinion, the reduce method is the most useful one. With it, we can transform our array into the result we need.

const data = [
    { state: 'France', city: 'Paris', visited: 'no' },
    { state: 'France', city: 'Lyon', visited: 'no' },
    { state: 'France', city: 'Marseille', visited: 'yes' },
    { state: 'Italy', city: 'Rome', visited: 'yes' },
    { state: 'Italy', city: 'Milan', visited: 'no' },
    { state: 'Italy', city: 'Palermo', visited: 'yes' },
    { state: 'Italy', city: 'Genoa', visited: 'yes' },
    { state: 'Germany', city: 'Berlin', visited: 'no' },
    { state: 'Germany', city: 'Hamburg', visited: 'yes' },
    { state: 'USA', city: 'New York', visited: 'yes' }
];

const result = data.reduce((accumulator, item) => {
  accumulator.states.push(item.state);
  accumulator.cities.push(item.city);
  return accumulator;
}, {
  states: [],
  cities: []
});

console.log(result);

// outputs

// cities: (10) ['Paris', 'Lyon', 'Marseille', 'Rome', 'Milan', 'Palermo', 'Genoa', 'Berlin', 'Hamburg', 'New York']
// states: (10) ['France', 'France', "France', 'Italy', "Italy', 'Italy', 'Italy', 'Germany', 'Germany', 'USA']
```
#### Shifting Elements
```
Data copying within the same array might seem pointless to some, and to be honest, I don't see a lot of use cases to do this. I can imagine this being useful in cases when we are building a drag&drop list with reordering enabled. We can use copyWithin to update the underlying data model for the list.

cities.copyWithin(0, 2, 3); // copy to index 0 element at index 2
console.log(cities); // outputs ['New York', 'London', 'New York', 'Barcelona', 'Madrid', 'San Francisco']

    NOTE: This method modifies the source array and only does a shallow coping thus handling objects should be done with care
```
#### Flattening
```
One of the new methods added to the array API is the method flat.

    This method creates a new array with all sub-array elements concatenated into it recursively up to the specified depth. The default depth is 1

This means we can get a single array as a result in a case when we have an array of arrays. Not every item of the source array needs to be an array. Array.flat is smart enough to figure that out.

let numbers = [1, 2, [3, 4]];
console.log(numbers.flat()); // outputs [1, 2, 3, 4]

I don't see this being used that often, but the reason I put it on this list is that I find it interesting the fact that it will remove all empty slots from our array. If you think of any other useful use case, feel free to write it in the comments section.

let numbers = [1, 2, [3, 4],, 5, 6,, [7,8]];
console.log(numbers.flat()); // outputs [1, 2, 3, 4, 5, 6, 7, 8]
```
