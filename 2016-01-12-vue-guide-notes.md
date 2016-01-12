You can bind class and style objects, usually to computed properties...

## binding classes

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

You can also bind to an `object` in data:

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

You can also bind to an `array` in data:

```
data: {
  classA: 'class-a',
  classB: 'class-b'
}
<div v-bind:class="[classA, classB]">
```
result: `<div class="class-a class-b"></div>`

You can also use ternary expressions to assign classes only when they return true:

`<div v-bind:class="[classA, isB ? classB : '']">`
result: `<div class="class-a class-b"></div>`

## binding styles

```
data: {
  styleObject: {
    color: 'red',
    fontSize: '13px'
  }
}
<div v-bind:style="styleObject"></div>
```

you can also bind to multiple style objects with an array:

`<div v-bind:style="[styleObjectA, styleObjectB]">`

You get autoprefixing for free.

## v-if, v-show, v-else

pretty self-explanatory

## v-for

rendering lists...

```
<ul id="example-1">
  <li v-for="item in items">
    {{ item.message }}
  </li>
</ul>
```

```javascript
var example1 = new Vue({
  el: '#example-1',
  data: {
    items: [
      { message: 'Foo' },
      { message: 'Bar' }
    ]
  }
})
```
Result:
```
• Foo
• Bar
```

inside `v-for` we have access to properties in the parent scope, plus a variable for the index or key:

```
<ul id="example-2">
  <li v-for="(index, item) in items">
    {{ parentMessage }} - {{ index }} - {{ item.message }}
  </li>
</ul>
```
```javascript
var example2 = new Vue({
  el: '#example-2',
  data: {
    parentMessage: 'Parent',
    items: [
      { message: 'Foo' },
      { message: 'Bar' }
    ]
  }
})
```
Result:
```
• Parent - 0 - Foor
• Parent - 1 - Bar
```

## template v-for

to render a block of multiple elements:

```
<ul>
  <template v-for="item in items">
    <li>{{ item.msg }}</li>
    <li class="divider"></li>
  </template>
</ul>
```

## track-by

If you're replacing an array of objects (e.g. with an API call) you can try to re-use any elements by using `track-by`:

```javascript
{
  items: [
    { _uid: '88f869d', ... },
    { _uid: '7496c10', ... }
  ]
}
```
```
<div v-for="item in items" track-by="_uid">
  <!-- content -->
</div>
```

















