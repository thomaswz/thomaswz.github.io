# The Nuxt Store

###### Created 22 April 2020, Updated 22 April 2020

This is a standard layout of the store.  
In Nuxt the store can have multiple files.

```javascript
// Recommended: Actions call mutations to update the state
const state = () => ({
  funtest: [],
});

// Mutuations are used to commit and track state changes.
// Standard practice to use FULL_CAPS for mutations.
const mutations = {
  SET_FUNTEST(state, payload) {
    state.funtest = payload;
  },
};

// actions are the "methods" which update the mutations, which update the state
const actions = {
  setfuntest(context, update) {
    context.commit('SET_FUNTEST', update);
  },
};

// getters are the "computed" properties which access the state. i.e. filter retrieve
const getters = {
  performfuntest(state) {
    return state.performfuntest;
  },
};

export default {
  state,
  mutations,
  actions,
  getters,
};
```
