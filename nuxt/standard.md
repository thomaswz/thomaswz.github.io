# Standard Nuxt Page

###### Created 24 April 2020, Updated 24 April 2020

The page can be templated with "vue" in VS Code

```javascript
<template>
  <div class="Main">
    <h1>Main</h1>
    <p>{{ funcalc }}</p>
    <p>{{ this.$store.getters.funfacts }}</p>
  </div>
</template>

<script>
export default {
  layout: '',
  components: '',
  // objects have to be declared in data in order for them to be reactive
  data () {
    return {
    }
  },
  /*
  computed properties use data properties, they should not change them... though can set them
  computed properties can run a calculation once and then only again if the inputs change
  computed properties must have a "return"
  */
  computed: {
    funcalc () {
      const a = 0
      return a
    }

  },
  // watchers observe and then react with other elements based on changing elements
  watch: {
    //   the function below updates the store
    funupdate () {
      this.$store.dispatch('funupdate', this.funcalc)
    }
  },
  // methods are used to change the underlying data
  methods: {
  }
}
</script>

<!-- Style should be globalised and not kept in the page -->
<style scoped>

</style>>

```
