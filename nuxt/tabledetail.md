# Table Detail

###### Created 23 May 2020, Updated 23 May 2020

## Table

I wanted to create a bootstrap table with a button-exposed detail row.

The table had to be created **manually** as I wanted all its cells to be individually reactive.
I thought that using the standard `<b-table>` would requirem deconstructing the date... that would be easy... but difficult to reconstruct later.

## Rows

I then had an issue creating the rows... I needed to iterate through the rows.

- I first put the `v-for` iteration on the rows, but the table needs **two** rows as the detail in one row will be limited to that cell's column width.
- I then put in a `div` and iterated on that... but the div then fits the table under the first column...
- I then put in a `template` and interated on that... but had an error on the `:keys=""` which are not accepted by the linter. (removing the `:key=""` messes with the `v-for` so a catch-22)
- this is solved by:
  - adding serialised bindings to the two rows: `<b-tr :key="'rows' + i ">` and `<b-tr :key="'detail' + i">`
  - updating the `.eslintrc.js` file in the `root` with: `'vue/html-self-closing': 'off' // Fix v-for/template/key bug`

## Code

### In the `.eslintrc.js` file:

```javascript
  rules: {
    'vue/html-self-closing': 'off' // Fix v-for/template/key bug
  }
```

### In the `.vue` file:

```javascript
<template>
  <div>
      <b-table-simple>
          <b-thead>
            <b-tr>
                <b-th>Column 01</b-th>
                <b-th>Column 02</b-th>
                <b-th>Column 03</b-th>
            </b-tr>
        </b-thead>
      <b-tbody>
          <template v-for="i in 5">
          <b-tr :key="'rows'+i" >
        <!-- below should be a variable, {{ `0${i}` }} but github does not like it-->
                <b-td>
                    Heading:{{ `0${i}` }}
                </b-td>
                <b-td>
                   <b-button
                        :class=" visible ? null : 'collapsed' "
                        :aria-expanded=" visible[`v0${i}`] ? 'true' : 'false' "
                        :aria-controls="collapse[`${i}`]"
                        @click="visible[`v0${i}`] = !visible[`v0${i}`]"
                        variant="info"
                    >Toggle Collapse</b-button>
                </b-td>
                <b-td>
                    Other: {{ `${i}` }}
                </b-td>
          </b-tr>
          <b-tr :key="'detail' + i">
              <b-td colspan="3">
                  <b-collapse
                        :id="collapse[`${i}`]"
                        v-model="visible[`v0${i}`]"
                        >
                        <b-textarea
                    rows="5"
                    :placeholder="`Please input the details for 0${i} here`"
                    :ref="`pDetails0${i}`"
                  />
                    </b-collapse>
              </b-td>
          </b-tr>
          </template>
      </b-tbody>
  </b-table-simple>
  </div>
</template>

<script>
export default {
    data() {
        return{
            visible: {
                v01: false,
                v02: false,
                v03: false,
                v04: false,
                v05: false
            },
            collapse: [
                'collapse-1',
                'collapse-2',
                'collapse-3',
                'collapse-4',
                'collapse-5'
                ]
        }
    }

}
</script>

<style>

</style>
```
