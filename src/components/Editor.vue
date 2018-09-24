<template>
  <div class="editor">
    <h1>エディター画面</h1>
    <button @click="logout"> ログアウト </button>
    <div​ class="editorWrapper">​
      <textarea​ class="markdown" v-model="markdown"></textarea>​
      <div class="preview" ​v-html="preview()"></div>
    </div​>
  </div>
</template>
<script>
import marked from 'marked';
export default {
  name: 'editor',
  props: ['user'],
  data () {
    return {
      markedown: '',
    }
  },
  methods: {
    logout: function() {
      firebase.auth().signOut();
    },
    preview: function() {
      return marked(this.markdown);
    }
  }
}
</script>
<style lang="scss">
.editorWrapper {
  display: flex;
}
.markdown {
  width: 50%;
  height: 500px;
}
.preview {
  width: 50%;
  text-align: left;
}
</style>
