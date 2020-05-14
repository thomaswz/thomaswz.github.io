# The Nuxt Store

###### Created 22 April 2020, Updated 7 May 2020

This is a standard layout of the store.  
In Nuxt the store can have multiple files.

## Multiple files in the store folder

Save the files i.e. `users.js` in the `/store` folder then import them into the store folder:

> note the `namespaced: true`

```javascript
import Vuex from 'vuex';
import users from './users';
import glossary from './glossary';

const createStore = () => {
  return new Vuex.Store({
    namespaced: true,
    modules: {
      users: users,
      glossary: glossary,
    },
  });
};

export default createStore;
```

## Store Layout (in `index.js` or `other.js` files)

```javascript
// Recommended: Actions call mutations to update the state
const state = () => ({
  funTest: [],
});

// Mutuations are used to commit and track state changes.
// Standard practice to use FULL_CAPS for mutations.
const mutations = {
  SET_FUNTEST(state, payload) {
    state.funTest = payload;
  },
};

// actions are the "methods" which update the mutations, which update the state
const actions = {
  setfunTest(context, update) {
    context.commit('SET_FUNTEST', update);
  },
};

// getters are the "computed" properties which access the state. i.e. filter retrieve
const getters = {
  getfunTest(state) {
    return state.funTest;
  },
};

export default {
  state,
  mutations,
  actions,
  getters,
};
```

## Simple Store Layout (in `index.js` or `other.js` files)

```javascript
const state = () => ({
  funTest: [],
});

const mutations = {
  SET_FUNTEST(state, payload) {
    state.funTest = payload;
  },
};

const actions = {
  setfunTest(context, update) {
    context.commit('SET_FUNTEST', update);
  },
};

const getters = {
  getfunTest: (state) => state.funTest,
};

export default {
  state,
  mutations,
  actions,
  getters,
};
```
