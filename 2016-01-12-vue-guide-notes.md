## assigning classes

Classes are bound to `values` in `data`:

```
data: {
  isA: true,
  isB: false
}
<div class="static" v-bind:class="{ 'class-a': isA, 'class-b': isB }"></div>
```
result:
`<div class="static class-a"></div>`

You can also bind to `objects` in data:

```
data: {
  classObject: {
    'class-a': true,
    'class-b': false
  }
}
<div v-bind:class="classObject"></div>

```
result:
`<div class="static class-a"></div>`


