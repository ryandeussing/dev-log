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

If you're replacing an array of objects (e.g. with an API call) you can try to re-use elements, of possible,  by using `track-by`:

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

## adding to array

you need to use `$set` when modifying a specific index position of an array:

```javascript
// same as `example1.items[0] = ...` but triggers view update
example1.items.$set(0, { childMsg: 'Changed!'})
```

## removing from an array

you can use `$remove`, which handles splicing for you:

`this.items.$remove(item)`

## displaying filtered/ordered results

when you don't need to change the data, but just want to filter or order elements on the page, you can:

- use a computed property that returns the filtered or sorted Array (more control)
- use `filterBy` or `orderBy` helpers (more convenient)

## methods + event handling

stop propagation: `<a v-on:click.stop="doThis"></a>`

prevent default: `<form v-on:submit.prevent="onSubmit"></form>`

chain modifiers: `<a v-on:click.stop.prevent="doThat">`

## key modifiers for common keys

submit on enter keyup: `<input @keyup.enter="submit">`
```
enter
tab
delete
esc
space
up
down
left
right
```

## form input bindings

`v-model` is syntax sugar for forms, creates 2-way binding for for elements, and auto-selects the right way to store data based on the form element (boolean, array, string, etc.)

you can use `v-bind` to bind values to dynamic properties: (here, `a` and `b` are keys on the `vm.data` object)

```
<input
  type="checkbox"
  v-model="toggle"
  v-bind:true-value="a"
  v-bind:false-value="b">
```

Here, `vm.pick` will not be `a`, but will be the value of `vm.a`:
`<input type="radio" v-model="pick" v-bind:value="a">`


### lazy

```
<!-- synced after "change" instead of "input" -->
<input v-model="msg" lazy>
```

### number

```
<!-- automatically persist input as numbers -->
<input v-model="age" number>
```

### debounce

```
<!-- set a min delay after each keystroke before update is performed -->
<input v-model="msg" debounce="500">
<!-- note: use vm.$watch() to react to data changes when using debounce -->
```

## transitions

lets you apply automatic transitions when elements are inserted or removed from the DOM. CSS classes are automatically added/removed to trigger CSS transitions/animations, you can also apply javascript hooks for DOM manipulation. 

`<div v-if="show" transition="my-transition"></div>`

You can use the `transition` attribute with
```
• v-if
• v-show
• v-for (triggered for insertion/romoval only)
• dynamic components
• On a componenent rood node, using Vue instance DOM methods (vm.$appendTo(el))
```

When an element with `transition` is added or removed, Vue will:

• Try to find a JavaScript transition hooks object registered either through `Vue.transition(id, hooks)` or passed in with the transitions option, using the id "#my-transition". If it finds it, it will call the appropriate hooks at different stages of the transition.

• Automatically sniff whether the target element has CSS transitions or CSS animations applied, and add/remove the CSS classes at the appropriate times.

• If no JavaScript hooks are provided and no CSS transitions/animations are detected, the DOM operation (insertion/removal) is executed immediately on next frame.

`<div v-if="show" transition="expand">hello</div>`

You need to define CSS rules for `.*-transition`, `.*-enter`, and `.*-leave` (see docs)

Available javascript hooks:

```javascript
Vue.transition('expand', {

  beforeEnter: function (el) {
    el.textContent = 'beforeEnter'
  },
  enter: function (el) {
    el.textContent = 'enter'
  },
  afterEnter: function (el) {
    el.textContent = 'afterEnter'
  },
  enterCancelled: function (el) {
    // handle cancellation
  },

  beforeLeave: function (el) {
    el.textContent = 'beforeLeave'
  },
  leave: function (el) {
    el.textContent = 'leave'
  },
  afterLeave: function (el) {
    el.textContent = 'afterLeave'
  },
  leaveCancelled: function (el) {
    // handle cancellation
  }
})
```

## custom transition classes let you use libraries like animate.css
see docs

## components

when using `Vue.extend()` (either explicitly, or under-the-hood when using vue-loader) you need your component `data` to be a function that returns values. Otherwise every instance of the component would have the same value.

## props

every component instance has its own isolated scope. You cannot directly reference parent data in a child component's template. You pass data down using `props`.

A child component needs to explicity declare the props it expects:

```javascript
Vue.component('child', {
  // declare the props
  props: ['msg'],
  // the prop can be used inside templates, and will also
  // be set as `this.msg`
  template: '<span>{{ msg }}</span>'
})
```

Then we can pass a string to it: `<child msg="hello!"></child>`

### html requires kebab-case

`camelCase` prop names are standard, but inside html you need to use the `kebab-case` equivalent:

```javascript
Vue.component('child', {
  // camelCase in JavaScript
  props: ['myMessage'],
  template: '<span>{{ myMessage }}</span>'
})
```

`<child my-message="hello!"></child>`

## dynamic props

you can use `v-bind` (or shorthand) to dynamically bind props to data on the parent. When data is updated, it will flow down to the child:

```
<div>
  <input v-model="parentMsg">
  <br>
  <child :my-message="parentMsg"></child>
</div>
```

## literal vs. dynamic

```
<!-- this passes down a plain string "foo" -->
<comp some-prop="foo"></comp>
```

```
<!-- this passes down a reference to data.foo -->
<comp :some-prop="foo"></comp>
```

## one-way data-binding is the default

but you can enforce a two-way (or a one-time) binding with the `.sync` and `.once` modifiers

```
<!-- default, one-way-down binding -->
<child :msg="parentMsg"></child>

<!-- explicit two-way binding -->
<child :msg.sync="parentMsg"></child>

<!-- explicit one-time binding -->
<child :msg.once="parentMsg"></child>
```
### note: if the prop being passed down is an Object or an Array, it is passed by reference. Mutating the Object or Array itself inside the child will affect parent state, regardless of the binding type you are using.

## prop validation

see docs for full details.

when re-using components, this is a good idea. You can also provide default values:

```javascript
Vue.component('example', {
  props: {
    // basic type check (`null` means accept any type)
    propA: Number,
    // a required string
    propB: {
      type: String,
      required: true
    },
    // a number with default value
    propC: {
      type: Number,
      default: 100
    }
  }
)};
```

```
Available types:
- String
- Number
- Boolean
- Function
- Object
- Array
```

## parent/child communicatin

a child component has access to its parent as `this.$parent`, the root Vue instance is available to all children as `this.$root`

each parent component has an array, `this.$children`, containing all it's child components

BUT: use props to get data, not the `this.$parent` - otherwise you can create a mess with children changing parent state.

## custom events

Vue instances have their own event system, apart from DOM events, that allows for communication in a component tree.

Each Vue instance is an event emitter that can:

```
• Listen to events using $on() (not the same as v-on in DOM!)

• Trigger events on self using $emit()

• Dispatch an event that propagates upward along the parent chain using $dispatch()

• Broadcast an event that propagates downward to all descendants using $broadcast()
```
see docs

### using v-on for custom events

`<child v-on:child-msg="handleIt"></child>`
With this, the parent no longer has to have an `events` option, just a `handleIt` method that will take care of the `child-msg` event.

## child component refs

even with props and events, sometimes you may need to directly access a child component in javascript. to do this you need to assign a reference id to the child using `v-ref`:

```
<div id="parent">
  <user-profile v-ref:profile></user-profile>
</div>
```

```javascript
var parent = new Vue({ el: '#parent' })
// access child component instance
var child = parent.$refs.profile
```

## content distribution with slots

lets us do this:

```
<app>
  <app-header></app-header>
  <app-footer></app-footer>
</app>
```

### single slot

Parent content will be discarded unless the child component template contains at least one `<slot>` outlet.

Anything originally inside the `<slot>` tags is considered fallback content. Fallback content is compiled in the child scope and will only be displayed if the hosting element is empty.

Take this template for `my-component`: 
```
<div>
  <h1>This is my component!</h1>
  <slot>
    This will only be displayed if there is no content
    to be distributed.
  </slot>
</div>
```
Here's parent markup including `my-component` AND content:
```
<my-component>
  <p>This is some original content</p>
  <p>This is some more original content</p>
</my-component>
```
Here's the result:
```
<div>
  <h1>This is my component!</h1>
  <p>This is some original content</p>
  <p>This is some more original content</p>
</div>
```

























