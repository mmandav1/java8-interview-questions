# Java8 Interview Questions & Answers

> Click :star:if you like the project. Pull Requests are highly appreciated. Follow me  for technical updates.


## Disclaimer

The questions provided in this repository are the summary of frequently asked questions across numerous companies. We cannot guarantee that these questions will actually be asked during your interview process, nor should you focus on memorizing all of them. The primary purpose is for you to get a sense of what some companies might ask — do not get discouraged if you don't know the answer to all of them ⁠— that is ok!

Good luck with your interview 😊

---

### Table of Contents

| No. | Questions |
|---- | ---------
|1  | [Java8 Features](#Java8-features) |
|2  | [What is prototype chain](#what-is-a-prototype-chain)|
|3  | [What is the difference between Call, Apply and Bind](#what-is-the-difference-between-call-apply-and-bind)|
|4  | [What is JSON and its common operations](#what-is-json-and-its-common-operations)|
|5  | [What is the purpose of the array slice method](#what-is-the-purpose-of-the-array-slice-method)|
|6  | [What is the purpose of the array splice method](#what-is-the-purpose-of-the-array-splice-method)|
|7  | [What is the difference between slice and splice](#what-is-the-difference-between-slice-and-splice)|
|8  | [How do you compare Object and Map](#how-do-you-compare-object-and-map)|
|9  | [What is the difference between == and === operators](#what-is-the-difference-between-==-and-===-operators)|
|10 | [What are lambda or arrow functions](#what-are-lambda-or-arrow-functions)|

1. ### https://github.com/learning-zone/java-interview-questions

   
      **[⬆ Back to Top](#table-of-contents)**

2. ### What is a prototype chain

    **Prototype chaining** is used to build new types of objects based on existing ones. It is similar to inheritance in a class based language. The prototype on object instance is available through **Object.getPrototypeOf(object)** or __proto__ property whereas prototype on constructors function is available through object.prototype.

    ![Screenshot](images/prototype_chain.png)

    **[⬆ Back to Top](#table-of-contents)**

3. ### What is the difference between Call, Apply and Bind

    The difference between Call, Apply and Bind can be explained with below examples,

    **Call:** The call() method invokes a function with a given `this` value and arguments provided one by one

    ```javascript
    var employee1 = {firstName: 'John', lastName: 'Rodson'};
    var employee2 = {firstName: 'Jimmy', lastName: 'Baily'};

    function invite(greeting1, greeting2) {
        console.log(greeting1 + ' ' + this.firstName + ' ' + this.lastName+ ', '+ greeting2);
    }

    invite.call(employee1, 'Hello', 'How are you?'); // Hello John Rodson, How are you?
    invite.call(employee2, 'Hello', 'How are you?'); // Hello Jimmy Baily, How are you?
    ```

    **Apply:** Invokes the function and allows you to pass in arguments as an array

    ```javascript
    var employee1 = {firstName: 'John', lastName: 'Rodson'};
    var employee2 = {firstName: 'Jimmy', lastName: 'Baily'};

    function invite(greeting1, greeting2) {
        console.log(greeting1 + ' ' + this.firstName + ' ' + this.lastName+ ', '+ greeting2);
    }

    invite.apply(employee1, ['Hello', 'How are you?']); // Hello John Rodson, How are you?
    invite.apply(employee2, ['Hello', 'How are you?']); // Hello Jimmy Baily, How are you?
    ```

    **bind:** returns a new function, allowing you to pass in an array and any number of arguments

    ```javascript
    var employee1 = {firstName: 'John', lastName: 'Rodson'};
    var employee2 = {firstName: 'Jimmy', lastName: 'Baily'};

    function invite(greeting1, greeting2) {
        console.log(greeting1 + ' ' + this.firstName + ' ' + this.lastName+ ', '+ greeting2);
    }

    var inviteEmployee1 = invite.bind(employee1);
    var inviteEmployee2 = invite.bind(employee2);
    inviteEmployee1('Hello', 'How are you?'); // Hello John Rodson, How are you?
    inviteEmployee2('Hello', 'How are you?'); // Hello Jimmy Baily, How are you?
    ```

    Call and apply are pretty interchangeable. Both execute the current function immediately. You need to decide whether it’s easier to send in an array or a comma separated list of arguments. You can remember by treating Call is for comma (separated list) and Apply is for Array. Whereas Bind creates a new function that will have `this` set to the first parameter passed to bind().

    **[⬆ Back to Top](#table-of-contents)**

4. ### What is JSON and its common operations

    **JSON** is a text-based data format following JavaScript object syntax, which was popularized by `Douglas Crockford`. It is useful when you want to transmit data across a network and it is basically just a text file with an extension of .json, and a MIME type of application/json
    **Parsing:** Converting a string to a native object

    ```javascript
    JSON.parse(text)
    ```

    Stringification: **converting a native object to a string so it can be transmitted across the network

    ```javascript
    JSON.stringify(object)
    ```

    **[⬆ Back to Top](#table-of-contents)**

5. ### What is the purpose of the array slice method

    The **slice()** method returns the selected elements in an array as a new array object. It selects the elements starting at the given start argument, and ends at the given optional end argument without including the last element. If you omit the second argument then it selects till the end. Some of the examples of this method are,

    ```javascript
    let arrayIntegers = [1, 2, 3, 4, 5];
    let arrayIntegers1 = arrayIntegers.slice(0,2); // returns [1,2]
    let arrayIntegers2 = arrayIntegers.slice(2,3); // returns [3]
    let arrayIntegers3 = arrayIntegers.slice(4); //returns [5]
    ```

    **Note:** Slice method won't mutate the original array but it returns the subset as a new array.

    **[⬆ Back to Top](#table-of-contents)**

6. ### What is the purpose of the array splice method

    The **splice()** method is used either adds/removes items to/from an array, and then returns the removed item. The first argument specifies the array position for insertion or deletion whereas the option second argument indicates the number of elements to be deleted. Each additional argument is added to the array. Some of the examples of this method are,

    ```javascript
    let arrayIntegersOriginal1 = [1, 2, 3, 4, 5];
    let arrayIntegersOriginal2 = [1, 2, 3, 4, 5];
    let arrayIntegersOriginal3 = [1, 2, 3, 4, 5];

    let arrayIntegers1 = arrayIntegersOriginal1.splice(0,2); // returns [1, 2]; original array: [3, 4, 5]
    let arrayIntegers2 = arrayIntegersOriginal2.splice(3); // returns [4, 5]; original array: [1, 2, 3]
    let arrayIntegers3 = arrayIntegersOriginal3.splice(3, 1, "a", "b", "c"); //returns [4]; original array: [1, 2, 3, "a", "b", "c", 5]
    ```

    **Note:** Splice method modifies the original array and returns the deleted array.

    **[⬆ Back to Top](#table-of-contents)**

7. ### What is the difference between slice and splice

    Some of the major difference in a tabular form

    | Slice | Splice |
    |---- | ---------
    | Doesn't modify the original array(immutable)  | Modifies the original array(mutable) |
    | Returns the subset of original array | Returns the deleted elements as array  |
    | Used to pick the elements from array | Used to insert or delete elements to/from array|

    **[⬆ Back to Top](#table-of-contents)**

8. ### How do you compare Object and Map

    **Objects** are similar to **Maps** in that both let you set keys to values, retrieve those values, delete keys, and detect whether something is stored at a key. Due to this reason, Objects have been used as Maps historically. But there are important differences that make using a Map preferable in certain cases.

    1. The keys of an Object are Strings and Symbols, whereas they can be any value for a Map, including functions, objects, and any primitive.
    2. The keys in Map are ordered while keys added to Object are not. Thus, when iterating over it, a Map object returns keys in order of insertion.
    3. You can get the size of a Map easily with the size property, while the number of properties in an Object must be determined manually.
    4. A Map is an iterable and can thus be directly iterated, whereas iterating over an Object requires obtaining its keys in some fashion and iterating over them.
    5. An Object has a prototype, so there are default keys in the map that could collide with your keys if you're not careful. As of ES5 this can be bypassed by using map = Object.create(null), but this is seldom done.
    6. A Map may perform better in scenarios involving frequent addition and removal of key pairs.

    **[⬆ Back to Top](#table-of-contents)**

9. ### What is the difference between == and === operators

    JavaScript provides both strict(===, !==) and type-converting(==, !=) equality comparison. The strict operators take type of variable in consideration, while non-strict operators make type correction/conversion based upon values of variables. The strict operators follow the below conditions for different types,
    1. Two strings are strictly equal when they have the same sequence of characters, same length, and same characters in corresponding positions.
    2. Two numbers are strictly equal when they are numerically equal. i.e, Having the same number value.
       There are two special cases in this,
       1. NaN is not equal to anything, including NaN.
       2. Positive and negative zeros are equal to one another.
    3. Two Boolean operands are strictly equal if both are true or both are false.
    4. Two objects are strictly equal if they refer to the same Object.
    5. Null and Undefined types are not equal with ===, but equal with ==. i.e,
        null===undefined --> false but null==undefined --> true

    Some of the example which covers the above cases,

    ```javascript
    0 == false   // true
    0 === false  // false
    1 == "1"     // true
    1 === "1"    // false
    null == undefined // true
    null === undefined // false
    '0' == false // true
    '0' === false // false
    []==[] or []===[] //false, refer different objects in memory
    {}=={} or {}==={} //false, refer different objects in memory
    ```

    **[⬆ Back to Top](#table-of-contents)**

10. ### What are lambda or arrow functions

    An arrow function is a shorter syntax for a function expression and does not have its own **this, arguments, super, or new.target**. These functions are best suited for non-method functions, and they cannot be used as constructors.

    **[⬆ Back to Top](#table-of-contents)**

     Below are the some of main applications of Object.assign() method,

     1. It is used for cloning an object.
     2. It is used to merge objects with the same properties.

     **[⬆ Back to Top](#table-of-contents)**


---

**[⬆ Back to Top](#table-of-contents)**

