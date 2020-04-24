# Images

###### Created 24 April 2020, Updated 24 April 2020

I got this from Renat Galyamov [Image binding in Vue](https://medium.com/@renatello/how-to-bind-img-src-in-vue-js-5690ac89c1bb)

There are two different ways:

```javascript
new Vue({
  el: "#app",
  data: {
    image: 'https://picsum.photos/id/1005/600/200'
  }
})
<div id="app">
  <h2>Image:</h2>
  <img :src="image" style="width:100%;" alt="">
</div>
```

or

```javascript
<template>
<div id="app">
  <h2>Dynamic image in Vue.js:</h2>
  <p v-if="userProfilePic"><img style="width:100%" :src="userProfilePic" alt=""></p>
  <p><a href="#" @click="getImage()">Get a dynamic image</a></p>
</div>
</template>

<script>
new Vue({
  el: "#app",
  data: {
    userProfilePic: null
  },
  methods: {
    getImage () {
      this.userProfilePic = 'https://picsum.photos/id/1005/600/200'
    }
  }
})
</script>
```
