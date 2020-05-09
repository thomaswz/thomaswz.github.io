# Date

###### Created 9 May 2020, Updated 9 May 2020

This is to set the **current** date as a default value in a bootstrap date input.

```javascript
    dateNowShow() {
      let dateObj = new Date();
      let month = ('0' + (dateObj.getMonth() + 1)).slice(-2);
      let day = ('0' + dateObj.getDate()).slice(-2);
      let year = dateObj.getFullYear();
      let newdate = year + "-" + month + "-" + day
      return newdate
```
