# Regex

###### Created 2 May 2020, Updated 2 May 2020

## Useful Regex to know

The following code removes all funny characters from a string. Note that the evaluation happens between the `[ ]` and the `^` means "Not". The end `gi` is for global i.e. multiple times and ignoring case.

````javascript
    let idMod = update
    idMod = idMod.replace(/[^a-zA-Z0-9_-]/gi, '')
    ```
````
