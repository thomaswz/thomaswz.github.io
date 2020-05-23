# Dynamic Routes

###### Created 20 May 2020, Updated 20 May 2020

## Overview

Variable page links can be created as follows:

- create a folder for the page link i.e. `/pages/terms`
- create a page in the main folder i.e. in the same directory as the "terms" folder with the **same** name as the folder i.e. `/pages/terms.vue`.
- in the "terms" folder, create a landing page i.e. `pages/terms/index.vue`.
- in the "terms" folder, create the variable link page with the `_` prefix i.e. `/pages/terms/_id.vue`.

Note that the official documentation refers to a .vue file **OR** a directory prefixed by an underscore.

## Accessing

The route can be accessed through `this.$route.params.{parameterName}` i.e. `this.$route.params.id`

## Directory examples

The directory will look like this:

```javascript
pages/
--| _terms.vue

or

pages/
--| terms/
-----| index.vue
-----| _id.vue
--| terms.vue

or

pages/
--| _terms/
-----| index.vue
-----| comments.vue
--| terms.vue

```
