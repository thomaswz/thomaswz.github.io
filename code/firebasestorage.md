# Firebase Database and Local Storage

###### Created 5 May 2020, Updated 5 May 2020

This refers to the Firebase "Realtime" Database, and working with it into local storage.

## Firebase Realtime Database

### Accessing the branches

Of the ways to get data, the `on()` will realtime update and the `once()` will fetch the data once.

See the code below:

```javascript
let _self = this;
// get all the terms in the dictionary
let query = firebase.database().ref('dictionary/').orderByKey();
```

The **`_self`** needs to be applied to access the reactive terms and formulas.
The above code is a standard way to access one of the branches in the Firebase Database.

The **`ref()`** will reference the branch in the database.

### Then extracting the branch data

> Note that all the data is returned in the branch

The next block of code:

```javascript
query.once('value').then(function (snapshot) {
  _self.terms = Object.keys(snapshot.val());
  _self.definitions = Object.values(snapshot.val());
  _self.dictionary = Object.entries(snapshot.val());
  sessionStorage.terms = JSON.stringify(_self.terms);
  sessionStorage.dictionary = JSON.stringify(_self.dictionary);
  sessionStorage.definitions = JSON.stringify(_self.definitions);
});
```

Firebase `query` needs to access the `'value'`, and then the `shapshot` needs can be parsed with modern javascript, but it has to have the **`val()`** method.

There is good Javascript help from modern language:

- `keys` gets the branch keys and should return an `[ Array ]`
- `values` gets the base data
- `entries` gets the `{ Object }` key value pairs

### Loading the page data

Due to the delays of getting data from firebase i.e. normal loading of data etc... it is best that it is called just before the page loads:

Note the code below... the `ssTerms()` refers to `sessionStorage(terms)`:

```javascript
async beforeMount() {
    await this.listTerms()
    await this.ssTerms()
    }
```

## Local Storage

> Its important to use **`sessionStorage`** as this cache is cleared when the browser page is closed. It stays if the page is refreshed. The **`localStorage`** is very difficult to clear... and the data remains indefinitely.  
> Both are very difficult to secure so there should be no confidential data recorded in either of these.

### Loading data into local storage

There are a number of ways to get data into the `sessionStorage`. I used the `sessionStorage.terms` with the **`.terms`** as the `sessionStorage` name.

Storage requires information loaded into it set for JSON i.e. `JSON.stringify('xxx')` go get data in.

### Getting data from local storage

Storage requires its data is parsed when being extracted i.e. `JSON.parse(sessionStorage.getItem('xxx'))`.
