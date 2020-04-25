# Global components

###### Created 25 April 2020, Updated 25 April 2020

These are useful - I am using them for Nav Bars... as I initially wanted to build functionality into the nav bar i.e. sign out etc...  
I decided against the functionality in the Nav Bar, but still like global components.

In the `plugins` folder, save a file called `global.js`. (Any name will do).

Call the plugins as below:

```javascript
import Vue from 'vue';

import NavAppOne from '~/components/NavAppOne';
import NavMain from '~/components/NavMain';

Vue.component('navAppOne', NavAppOne);
Vue.component('navMain', NavMain);
```

then register the `global.js` folder in `nuxt.config.js` as a `plugin`:

```javascript
 plugins: [
    { src: "~/plugins/global.js" },
  ],
```

I learnt this from this [Nuxtjs Github Issue](https://github.com/nuxt/nuxt.js/issues/421)
