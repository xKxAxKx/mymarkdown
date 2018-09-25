<template>
  <div id="app">
    <!-- <Home v-if="!isLogin"></Home>
    <Editor v-if="isLogin" :user="userData"></Editor> -->
    <Editor></Editor>
  </div>
</template>
<script>
import Home from './components/Home.vue';
import Editor from './components/Editor.vue';

export default{
  name: 'app',
  data() {
    return {
      isLogin: false,
      userData: null,
    }
  },
  created: function() {
    firebase.auth().onAuthStateChanged(user => {
      console.log(this.isLogin);
      if(user) {
        this.isLogin = true;
        this.userdata = user;
      } else {
        this.isLogin = false;
        this.userdata = null;
      }
    })
  },
  components: {
    'Home': Home,
    'Editor': Editor,
  },
}
</script>
