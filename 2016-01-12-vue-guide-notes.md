##Dynamically setting classes

```javascript
data: {
  isA: true,
  isB: false
}
```


    <div class="static" v-bind:class="{ 'class-a': isA, 'class-b': isB }"></div>
