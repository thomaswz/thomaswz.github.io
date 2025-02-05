# Firebase

###### Created 28 Jan 2021, Updated 28 Jan 2021

# Overview

Firebase is a "serverless" environment. It allows for a lot of great built in features such as authorisation, database management and google analytics.

# Contents

[Back to landing](../landing.md)

_This document_
[Setup](#setup)
[Auth}](#authorisation)

_Other pages:_
[Firebase Functions](./firebasefunctions.md)

# Local

This refers to the local machine.

## Setup

I have found the docs a bit confusion. There are a lot of flavours.  
I have added it as follows: 

# Authorisation

There are a lot of authentication options i.e. email, phone etc.

## Auth State

There are two states i.e. authenticated or not authenticated.
There are a number of scenarios:

- Authenticating i.e. signing in or signing out
- Staying authenticated
  - upon sign in
  - upon opening / closing / refreshing browser
  - navigating different pages

## Client and Server

Note that Server refers to Nuxt i.e. SSR or server side rendering.
There are three storages forms that I am aware of:

- local storage - which is in the client
- cookies - which can be passed to the client or browser
- service workers - I am not sure exactly what these refer to, but they can work on client or ssr

## Role management

There are the following scenarios:

- team / employee i.e. self
- manager i.e. self and manager
- team i.e. group of self and manager
- admin i.e. all

Role management will need to be setup:

- on the client through route management i.e. can't access pages
- on the database server i.e. can't access information

> Note that client authoristion are locks on gates (to stop honest men). The server data protection is where the best protection occurs.

# Example

This example has been put together from Nuxt:
[Nuxt Firebase](https://firebase.nuxtjs.org/)
[Nuxt Firebase Demo on Github](https://github.com/lupas/nuxt-firebase-demo)
Note that I have also downloaded the Github version.

##### [Back to Top](#firebase)
