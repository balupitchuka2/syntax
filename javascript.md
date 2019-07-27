
### Array Operations Cheat Sheet

An array is a list-like object with extensive use cases. The most common, in my opinion, are described in this cheat sheet.
Create a new array

let cars = ['Mazda', 'Ford', 'BMW'];
// or
let cars = new Array('Mazda', 'Ford', 'BMW');

console.log(cars); // outputs ['Mazda', 'Ford', 'BMW']

Item access

let car = cars[1];
console.log(car); // outputs 'Ford'

    Items are accessed via index. Indexing starts at 0

Add new item at the end of an array

let newLength = cars.push('Opel');
console.log(cars); // outputs ['Mazda', 'Ford', 'BMW', 'Opel']

    Method push returns the new length of an array. In our example, it will return the number 4

Add new item at the beginning of an array

let newLength = cars.unshift('Renault');
console.log(cars); // outputs ['Renault', 'Mazda', 'Ford', 'BMW', 'Opel']

    Method unshift returns the new length of an array. In our example, it will return the number 5

Remove an item from the end of an array

let removedItem = cars.pop();
console.log(cars); // outputs ['Renault', 'Mazda', 'Ford', 'BMW']

    Method pop returns the removed item. In our example, it will return the text 'Opel'

Remove an item from the front of an array

let removedItem = cars.shift();
console.log(cars); // outputs ['Mazda', 'Ford', 'BMW']

    Method shift returns the removed item. In our example, it will return the text 'Renault'

Remove an item from the specific position

let removedItem = cars.splice(2, 1);
console.log(cars); // outputs ['Mazda', 'Ford']

    Method splice returns the removed items. In our example, it will return an array with one item ["BMW"]

Add an item at the specific position

let removedItem = cars.splice(1, 0, 'BMW');
console.log(cars); // outputs ['Mazda', 'BMW' 'Ford']

    The code above will insert a new item (BMW) at the position 1. The second parameter is the number of items we want to delete. After calling splice, the returned array will be empty because we didn't delete anything (0 was provided as the second parameter)

Replace an item at the specific position

let removedItem = cars.splice(2, 1, 'Renault');
console.log(cars); // outputs ['Mazda', 'BMW', 'Renault']

    The method splice, in this case, will return an array with one item ['Ford']

Reverse an array

let carsRev = cars.reverse();
console.log(cars); // outputs ['Renault', 'BMW', 'Mazda']

    NOTE: reverse method WILL MODIFY the original array

Sorting

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

Filtering

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

Find the specific item or its index

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

