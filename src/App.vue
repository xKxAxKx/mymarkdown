<template>
  <div id="app">
    <Home v-if="!login"></Home>
    <Editor v-if="login"></Editor>
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
  components: {
    'Home': Home,
    'Editor': Editor,
  },
  created: function() {
    firebase.auth().onAuthStateChanged(user => {
      console.log(user);
      if(user) {
        this.isLogin = true;
      } else {
        this.isLogin = false;
      }
    })
  }
}
</script>