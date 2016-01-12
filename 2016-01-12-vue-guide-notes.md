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


