<template>
  <div id="post">
    <p id="post-text">{{text}}</p>
  </div>
</template>
<script>
export default {
  name: "Post",
  props: ["text"]
};
</script>
<style scoped>
#post {
  width: 320px;
  height: 60px;
  border: 1px solid gray;
  margin: 4px;
  padding: 4px;
  box-sizing: border-box;
}
#post-text {
  margin: 0;
  text-align: left;
}
</style>

