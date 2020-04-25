# This

###### Created 25 April 2020, Updated 25 April 2020

## why is there an `undefined` message

`this` applied to the context of the function in which it is nested.

I found the issue in firebase authentication:

```javascript
methods: {
        loginUsers () {
          firebase.auth()
          .signInWithEmailAndPassword(this.email, this.password)
          .then(
            setTimeout(function(){ this.$router.push('/main')}, 2000))
          .catch(function(error) {
            // Handle Errors here.
            var errorCode = error.code;
            var errorMessage = error.message;
            // ...
            console.log(errorCode, errorMessage)
            });
        }
    }
```

The `this` is undefined as it is nested in the firebase function and so cannot see the light of day.  
Now context should have applied i.e. the nested function has access to all of its parents... but in my ignorance, I surmise that the context is in firebase and not the page's javascript.

to solve it, there are a number of ways... either using `.bind` or `_self`. I used the latter:

```javascript
loginUsers () {
          let _self = this

          firebase.auth()
          .signInWithEmailAndPassword(this.email, this.password)
          .then(
            setTimeout(function(){ _self.$router.push('/main')}, 2000))
          .catch(function(error) {
            // Handle Errors here.
            var errorCode = error.code;
            var errorMessage = error.message;
            // ...
            console.log(errorCode, errorMessage)
            });
        }
```
