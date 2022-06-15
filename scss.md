_* This rule is not the best practice but the one that we (developers at ownego) think is most suited for better software development.

***
### RESOURCE
***
CSS code guide: see [here][mdo code guide css]
BEM: see [here][bem doc]

***
### NAMING CONVENTION
***
1- Name classes using BEM principles, see [here][bem naming convention]

For example

```
.class-name: block
.class-name__child-class-name: element of block
.class-name--modifier: block's modifier (normal)
.class-name--is-active: block's modifier for state (special)
.class-name--has-something: block's modifier for state (special)
.js-class-name: for using as selector in javascript, don't use css class
```

2- Use kebab-case for scss variables, mixins.

3- All scss variables should be placed in _variables.scss

***
### SPECIFICITY
***
1- Don't use **id** to style.

```scss
// Not good
#idName {
  // some styles
}

// Good
[id="idName"] {
  // some styles
}
```

***
### NESTED
***
1- Avoid contextual styles. Use modifier as much as you can.

```scss
// Not good
.blog--featured {
  .banner {
    // some styles
  }
}

// Good
.banner--featured {
  // some styles
}
```

2- Keep style of block in same place. When a block modifier style effect an element, better keep style of the element inside block modifier (of course only in case you can't use a modifier for that element).

```scss
// Not good
.blog__title {
  // some styles

  .blog--featured & {
    // some styles
  }
}

// Good
.blog--featured {
  .blog__title {
    // some styles
  }
}
```

***
### MEDIA QUERY
***

```scss
// Not good
.blog {
  // some styles
}

@media (...) {
  .blog {
    // some styles
  }
}

// Good
.blog {
  // some styles

  @media (...) {
    // some styles
  }
}
```

***
### COMMENT
***
See [here][scss comment]

***
### DECLARATION ORDER
***
A bit different with mdo code guide above.

```scss
.class-name {
  // only extend from %placeholder
  // avoid extending from class as much as possible
  // only extend from class when you know exactly how sass @extend works
  @extend %placeholder;

  @include other-than-prefix-mixin();

  @include prefix-mixin();

  // Float
  float: left;

  // Positioning
  position: absolute;
  top: 0;
  right: 0;
  bottom: 0;
  left: 0;
  z-index: 1;

  // Box-model
  display: block;
  width: 100%;
  height: 100%;
  margin: 0;
  padding: 0;
  border: 0;
  background: none;

  // Typo
  font-family: sans;
  font-size: 14px;
  font-weight: 400;
  ...
  line-height: 1;
  text-align: center;
  text-transform: uppercase;
  ...
  color: $black;

  // Misc
  visibility: visible;
  overflow: hidden;

  // media query
  @media (...) {
    // some styles
  }

  // state
  &:active,
  &:focus,
  &:hover {
    // some styles
  }

  // modifiers, only nest if needed
  &.class-name--is-active {
    // some styles

    // media query
    @media (...) {
      // some styles
    }
  }

  &.class-name--has-something {
    // some styles

    // media query
    @media (...) {
      // some styles
    }
  }

  // only nest if needed
  .class-name__children {
    // some styles

    // media query
    @media (...) {
      // some styles
    }
  }
}
```



[mdo code guide css]: http://codeguide.co/#css
[bem doc]: https://en.bem.info/methodology/
[bem naming convention]: https://github.com/Shopify/css/tree/master/building-a-component
[scss comment]: https://github.com/Shopify/css/tree/master/commenting

