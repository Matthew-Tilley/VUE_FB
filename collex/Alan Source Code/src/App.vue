<template>
  <div id="app">
    <div v-for="item in items" :key="item.id">
      <img v-bind:src="imgpath(item)" />
      <span></span>
      <a v-bind:href="item.pageurl" target="_blank">
        <h1>{{item.title}}</h1>
        <h2>{{item.author}}</h2>
      </a>

    </div>
  </div>
</template>

<script>
//Get category ID from URL.
let catid = parseInt(window.location.href.split("=").pop());
//import HelloWorld from './components/HelloWorld'
import Firebase from "firebase";
let config = {
  apiKey: "AIzaSyAkHpfD2q1Wnx3JypsxLwhsUEovV1CD5Cg",
  authDomain: "collex-645e1.firebaseapp.com",
  databaseURL: "https://collex-645e1.firebaseio.com",
  projectId: "collex-645e1",
  storageBucket: "collex-645e1.appspot.com",
  messagingSenderId: "499076192990"
};
let app = Firebase.initializeApp(config);
let db = app.database();
let itemsRef = db.ref("items");
export default {
  name: "app",
  firebase: {
    //Filter by the catefory id that was passed in URL.
    items: itemsRef.orderByChild('categoryid').equalTo(catid)
  },
  methods: {
    imgpath: function(i) {
      return "/static/images/" + i.imgname + ".jpg";
    }
  }
};
</script>

<style scoped>
#app {
  padding:110px 0 60px 0;
  display: flex;
  flex-direction: row;
  justify-content: center;
  flex-wrap: wrap;
}
#app div {
  width: 300px;
  height: 185px;
  border: solid 1px gray;
  border-radius: 2px;
  margin: 0.5em;
  box-shadow: 2px 2px 2px silver;
  position: relative;
}
#app div img {
  position: absolute;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  border-radius: 2px;
  z-index: 10;
}
#app div span {
  display: block;
  position: absolute;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  background: linear-gradient(black, transparent);
  z-index: 15;
}
#app div h1 {
  margin: 2px 0 0 8px;
  font-size: 16pt;
  color: white;
}
#app div h2 {
  margin: 2px 0 0 8px;
  font-size: 12pt;
  color: white;
}
#app div a {
  display: block;
  position: absolute;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  text-decoration: none;
  color: black;
  z-index: 30;
}
</style>
