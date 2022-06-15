_* This rule is not the best practice but the one that we (developers at ownego) think is most suited for better software development.

***
### RESOURCE
***
Airbnb style guide: see [here][airbnb style guide]

***
### SOME COMMON RULES
***

_Highly recommend reading full airbnb guide. Below is just some common rules that are extracted from that guide._

1- Do not use `new` keyword. Use literal syntax instead.

```
// Not good
var newObj = new Object();
var newArr = new Array();

// Good
var newObj = {};
var newArr = [];
```

2- Copy `Array` or `Object`.
_Be careful when working with `Array` or `Object`. If you use normal assignment or shallow copy, you only work on a reference to original value._

  - **Array**:
    * Shallow copy: use javascript function slice(). See [here][mdn slice]. (`jQuery.extend()` is ok too)

    ```
    var srcArr = ['abc', 'def', 'ghi'];
    var destArr = srcArr.slice();

    console.log(destArr);

    // output
    // ['abc', 'def', 'ghi']
    ```
    * Deep copy: use `jQuery.extend()`. See example below.
  - **Object**:
    For both shallow and deep copy use `jQuery.extend()` or write your own function (not recommend). [More details][jquery extend]
    ```
    var srcObj = {
      apple: 0,
      banana: {
        price: 50,
        weight: 10
      },
      cherry: 100
    };
    var destObj = $.extend({}, srcObj);

    console.log(destObj);

    // output
    // Object destObj
    // {
    //   apple: 0,
    //   banana: {
    //     price: 50,
    //     weight: 10
    //   },
    //   cherry: 100
    // }
    ```

3- Use `Array.push()`.

```
var arr = [];

// Not good
arr[arr.length] = 'someValue';

// Good
arr.push('someValue');
```

4- Use one `var` for each variable.

**Advantage:**

  - Easier when add/remove a variable
  - No need to worry about `,` or `;`
  - Easy to convert to es6

Also avoid unassigned variable declaration.

5- Comparison and Equality
See [here][blog comparison]

6- Conditional statements format

```
// if/else
if (condition) {
  // do something
} else if (another condition) {
  // do something
} ... {
  // some stuff
} else {
  // do something
}

// switch
switch (srcTarget) {
  case value1:
    // do something
    break;
  ...
  default:
    // do something
}
```



[airbnb style guide]: https://github.com/airbnb/javascript
[mdn slice]: https://developer.mozilla.org/en/docs/Web/JavaScript/Reference/Global_Objects/Array/slice
[jquery extend]: https://api.jquery.com/jquery.extend
[blog comparison]: https://javascriptweblog.wordpress.com/2011/02/07/truth-equality-and-javascript

