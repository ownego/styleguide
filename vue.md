_* This rule is not the best practice but the one that we (developers at ownego) think is most suited for better software development.

***
### RESOURCE
***
Eslint plugin vue: see[here][eslint plugin vue]

***
### SOME COMMON RULES
***

1- Only use `reactive` with object.

```
// Bad
const reactiveObj = reactive(primitive data types);
const reactiveArr = reactive([]);

// Good
const reactiveObj = reactive({ id: 1 });
const reactiveArr = reactive({ array: [] });
```

2- If you want to reassign value for an object

```
// Bad
const objectToReassign = reactive({ b: 1 });

objectToReassign = { a: 2 };

// Good
const objectToReassign = ref({ b: 1 });

objectToReassign.value = { a: 2 };
```

3- Avoid using destructuring

Example with ref see [here][no-ref-object-destructure]
```
import { ref } from 'vue'
const count = ref(0)
const v1 = count.value /* ✗ BAD */
const { value: v2 } = count /* ✗ BAD */
const v3 = computed(() => count.value /* ✓ GOOD */)
const v4 = fn(count.value) /* ✗ BAD */
const v5 = fn(count) /* ✓ GOOD */
const v6 = computed(() => fn(count.value) /* ✓ GOOD */)
```

Example with props see [here][no-setup-props-destructure]
```
<script>
export default {
  /* ✓ GOOD */
  setup(props) {
    watch(() => {
      console.log(props.count)
    })

    return () => {
      return h('div', props.count)
    }
  }
}
</script>

```
[eslint plugin vue]: https://eslint.vuejs.org/rules/no-setup-props-destructure.html
[no-setup-props-destructure]: https://eslint.vuejs.org/rules/no-setup-props-destructure.html
[no-ref-object-destructure]: https://eslint.vuejs.org/rules/no-ref-object-destructure.html#vue-no-ref-object-destructure