<template>
  <div id="app">

    <div v-for="item in items" :key="item.id">

      <img v-bind:src="imgpath(item)">
      <a v-bind:href="item.pageurl" alt="">
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

  methods: {
    imgpath: function(i) {
      return "../static/images/" + i.imgname + ".jpg";
    },

  }
  

}
</script>

<style scoped>

#app div {
  width: 300px;
  height: 185px;
  border: solid 1px gray;
  border-radius: 2px;
  margin: .5em;
  box-shadow: 2px 2px silver;
}

</style>


