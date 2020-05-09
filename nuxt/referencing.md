# Referencing nested properties and converting them to objects

###### Created 2 May 2020, Updated 2 May 2020

## Overview

This is crucial to accessing nested properties in Vue i.e. nested form groups.  
They can be accessed through the `$ref` property, by adding a `ref = 'happy'` method to the property.

They will be accessed as `Arrays`, which can then be turned into `Objects`.

## Mixin

A good practice is to make this a `mixin`. A `mixin` is reusable JS function.

This `mixin` will return **all** of the `ref` items in the page as an Object.

### Templase

In the `<template>`:

> each `ref` must be **unique**, otherwise the code below will only access the last `ref` of the like reference. I tried many iterations and could not access all the same item `ref`.

```javascript
              <!-- content is accessed through the ref -->
              <b-form-input
                :id="content.vm"
                ref="happy"
                class="form-control"
                :value="content.vm"
                :placeholder="content.placeholder"
              />
```

### Script

In the `<script>`:

```javascript
import makeObjectsFromArrays from '@/mixins/refobjectsarray';

export default {
  mixins: [makeObjectsFromArrays],
  methods: {
    getContentrefs() {
      return this.makeObjectsFromArrays();
    },
  },
};
```

### Create a file for this function

Code in `@/mixin/refobjectsarray.js`:

```javascript
methods: {
export default {
  methods: {
    makeObjectsFromArrays() {
      // put it into this.$nextTick() if there are issues
      let refs = {}
      let columns = []
      let rows = []
      let result = {}
      // get the unique refs
      refs = this.$refs
      // put the refs keys into an array
      columns = Object.keys(refs)
      // make an object of the values note that some can be nested so the if
      for (let i in columns) {
        if (refs[`${columns[i]}`].localValue === undefined) {
          rows.push(refs[`${columns[i]}`][0].localValue)
        } else rows.push(refs[`${columns[i]}`].localValue)
      }
      // form the new array of the refs entries i.e. keys and values
      columns.forEach((key, i) => (result[key] = rows[i]))
      // log the result
      return result
    }
  }
}
```

### Extending

This file could be created as a global function if the mixin was referenced in the `nuxt.config.js` folder.
