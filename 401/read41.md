# React Native
## Review, Research, and Discussion
Compare and Contrast Redux Toolkit with Redux “Ducks” Ducks is a way to bundle reducers, action types, and actions into the same file. Rather than splitting up related code, it can be packaged into redux modules. Redux Toolkit's goal is to help simplify common Redux use cases. It is not intended to be a complete solution for everything you might want to do with Redux, but it should make a lot of Redux-related code you need to write a lot simpler. Redux Toolkit exports several individual functions that you can use in your application, and adds in dependencies on some other packages that are commonly used with Redux.

What is the principle advantage of Redux Toolkit Helps to solve three major problems with Redux: configuring a Redux store, adding numerous packages to get Redux to things, and removing unnecessary or boilerplate code.

## Vocabulary Terms
Redux Toolkit slices: Redux slice is a collection of reducer logic and actions for a single feature of application. Redux state is typically organized into slices, defined by the reducers that are passed to combineReducers

Namespace: Programming paradigm of providing scope to identifiers (names of types, functions, variables, etc) to prevent collisions between them. JavaScript does not provide namespace by default. However, we can replicate this functionality by making a global object which can contain all functions and variables.

## Preparation Materials
###  react native
open source framework for building Android and iOS applications using React
"Views" are the building blocks of iphone and android apps
React native allows for developing "native apps" that would otherwise be written in Kotlin or Java for Android and Swift or Obective-C for iOS
Core components, essential ready to use native components already built and available
### react native basics
import { Text, View } from 'react-native';
Native components: View, Text, Image, Button, StyleSheet
Resorces : 
* [Next.js - Dynamic Routes](https://nextjs.org/learn/basics/dynamic-routes)
* [Next.js - Deployment](https://nextjs.org/learn/basics/deploying-nextjs-app)
* Optional - [Next.js 10 is here](https://www.youtube.com/watch?v=JWCS5IdECVI)
* [Next.js - Static File Serving](https://nextjs.org/docs/basic-features/static-file-serving)