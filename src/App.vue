<template>
  <div id="app">
    <button @click="visible = !visible">点击</button>
    <message-box-warning
      title="标题"
      :visible.sync="visible"
      @cancel="visible = false"
      @ok="visible = false"
    />
  </div>
</template>

<script>
import MessageBoxWarning from "./components/message-box-warning/message-box-warning.vue";

export default {
  name: "App",
  data() {
    return {
      visible: false,
    };
  },
  components: { MessageBoxWarning },
};
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
