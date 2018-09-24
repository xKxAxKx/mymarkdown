<template>
  <div id="app">
    <Home v-if="!login"></Home>
    <Editor v-if="login" :user="userData"></Editor>
  </div>
</template>
<script>
import Home from './components/Home.vue';
import Editor from './components/Editor.vue';
export default{
  name: 'app',
  data() {
    return {
      login: false
    }
  },
  created: function() {
    firebase.auth().onAuthStateChanged(user => {
      console.log(user);
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