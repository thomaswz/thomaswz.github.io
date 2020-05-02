# Referencing nested properties and converting them to objects

###### Created 2 May 2020, Updated 2 May 2020

This is crucial to accessing nested properties in Vue i.e. nested form groups.  
They can be accessed through the `$ref` property, but adding a `ref = 'happy'` method to the property.

They will be accessed as `Arrays`, which can then be turned into `Objects`.

Code in HTML template:

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

Code in Script:

```javascript
 methods: {
    getContentrefs () {
      const columns = []
      const rows = []
      const contents = this.$refs.happy
      // access content through the ref into the DOM
      for (let i = 0; i < contents.length; i++) {
        columns.push(contents[i].id)
        rows.push(contents[i].localValue)
      }
    //   Create an Object from the Arrays
      const result = rows.reduce(function (result, field, index) {
        result[columns[index]] = field
        return result
      }, {})

      console.log(columns, rows, result)
      return rows
    }
  }
```
