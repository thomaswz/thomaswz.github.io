# The Nuxt Store

###### Created 22 April 2020, Updated 26 April 2020

This is a standard layout of the store.  
In Nuxt the store can have multiple files.

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
