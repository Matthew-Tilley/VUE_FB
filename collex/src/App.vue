<template>
  <div id="app1">

    <div v-for="item in items" :key="item.id">
      <a href="{{item.pageurl}}">
      <h1>{{item.title}}</h1>
      <h2>{{item.author}}</h2>
      </a>
    </div>

  </div>

</template>

<script>
//import HelloWorld from './components/HelloWorld'
import Firebase from 'firebase';

let config = {

    apiKey: "AIzaSyBZyil-JrhViIeivyyEp6UhWfHL2ReVSCE",
    authDomain: "collex-e1ab3.firebaseapp.com",
    databaseURL: "https://collex-e1ab3.firebaseio.com",
    projectId: "collex-e1ab3",
    storageBucket: "collex-e1ab3.appspot.com",
    messagingSenderId: "972126320719",

}

let app = Firebase.initializeApp(config);
let db = app.database();
let itemsRef = db.ref("items");

export default {
  name: 'App',

  firebase: {
    items: itemsRef,
  },
  

}
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
