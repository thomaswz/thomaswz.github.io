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
      return this.makeObjectsFromArrays('happy');
    },
  },
};
```

### Create a file for this function

Code in `@/mixin/refobjectsarray.js`:

```javascript
methods: {
  export default {
    makeObjectsFromArrays() {
      const columns = [];
      const rows = [];
      const contents = this.$refs.happy;
      // access content through the ref into the DOM
      for (let i = 0; i < contents.length; i++) {
        columns.push(contents[i].id);
        rows.push(contents[i].localValue);
      }
      //   Create an Object from the Arrays
      const result = rows.reduce(function (result, field, index) {
        result[columns[index]] = field;
        return result;
      }, {});

      console.log(columns, rows, result);
      return rows;
    },
  };
}
```

### Extending

This file could be created as a global function if the mixin was referenced in the `nuxt.config.js` folder.
