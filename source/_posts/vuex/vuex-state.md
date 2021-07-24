---
title: Vuex - State
date: 2021-07-24 16:46:53
cover: https://i.imgur.com/gHGilay.png
categories:
- Web Development
- Vuex
tags:
- Vuex
toc: true
---

## 1. Single State Tree
- A `single state tree` is a single object which Vuex uses to store all your application level state.
- It also serves as the `single source of truth`.

<!-- more -->

---

## 2. Getting Vuex State into Vue Components
By providing the `store` option to the `root instance`, the store will be injected into all child components of the root and will be available on them as `this.$store`.

```javascript
const Counter = {
  template: `<div>{{ count }}</div>`,
  computed: {
    count () {
      return this.$store.state.count
    }
  }
}

// root instance
const app = new Vue({
  el: '#app',
  // provide the store using the "store" option.
  // this will inject the store instance to all child components.
  store,
  components: { Counter },
  template: `
    <div class="app">
      <counter></counter>
    </div>
  `
})
```
---
## 3. The `mapState` Helper
When we want to add multiple store state properties to a component, `mapState` helper is the sugar syntax which would help us achieve that easily.

`mapState` accepts either `array` or `object` as its argument and would return an `object`.

### 3.1. `Array` as an argument 
```javascript
// below code lives in the file where our component lives

import { mapState } from 'Vuex'

export default {
  computed: mapState([
    // map this.count to store.state.count
    'count'
  ])
}
```

The above code is equivalent to below:
```javascript
import { mapState } from 'Vuex'

export default {
  computed: {
    count () {
      return this.$store.state.count
    }
  }
}
```

### 3.2. `Object` as an argument

```javascript
/ below code lives in the file where our component lives

import { mapState } from 'Vuex'

export default {
  // ...
  computed: mapState({
    // arrow functions can make the code very succinct!
    count: state => state.count,

    // passing the string value 'count' is same as `state => state.count`
    countAlias: 'count',

    // to access local state with `this`, a normal function must be used
    countPlusLocalState (state) {
      return state.count + this.localCount
    }
  })
}
```

The above code is equivalent to below:
```javascript
import { mapState } from 'Vuex'

export default {
  computed: {
    count () {
      return this.$store.state.count
    },

    countAlias () {
        return this.$store.state.count
    },

    countPlusLocalState () {
        return this.$store.state.count + this.localCount
    }
  }
}
```

Reference:
- [`mapState` API](https://vuex.vuejs.org/api/#mapstate)
- [Defining methods in an object](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Guide/Working_with_Objects#defining_methods)
- [Discussion from Vuejs Forum](https://forum.vuejs.org/t/dont-understand-how-to-use-mapstate-from-the-docs/14454/18)