<template>
  <div id="app">
    <form id="post-form">
      <textarea id="post-form-input" v-model="inputText"/>
      <button type="button" id="post-form-button" @click="sendPost">投稿</button>
    </form>
    <post v-for="post in reversePosts" :key="post.id" :text="post.text"/>
  </div>
</template>

<script>
import Post from "./components/Post.vue";

export default {
  name: "app",
  updated: function() {
    console.log(this.posts);
  },
  data: function() {
    return {
      inputText: "",
      currentId: 0,
      posts: []
    };
  },
  computed: {
    reversePosts: function() {
      return this.posts.slice().reverse();
    }
  },
  methods: {
    sendPost: function() {
      this.posts = [
        ...this.posts,
        {
          id: this.currentId++,
          text: this.inputText
        }
      ];
    }
  }
};
</script>

<style>
#app {
  font-family: "Avenir", Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
  display: flex;
  flex-direction: column;
  align-items: center;
}
#post-form {
  width: 320px;
  height: 160px;
  display: flex;
  flex-direction: column;
}
#post-form-input {
  height: 120px;
  resize: none;
}
#post-form-button {
  width: 80px;
  height: 24px;
  background: skyblue;
  font-size: 16px;
  color: white;
  margin: auto;
  border: none;
  border-radius: 2px;
  outline: none;
}
</style>
