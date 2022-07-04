<template>
  <div id="app">
    <img alt="Vue logo" src="./assets/logo.png" />
    <p style="color: red">扎不多的了</p>
    <p style="color: orange">扎不多的了</p>
    <p style="color: slateblue">扎不多的了</p>
    <p style="color: green">扎不多的了</p>
    <p style="color: blue">扎不多的了</p>
    <HelloWorld msg="Welcome to Your Vue.js App" />
  </div>
</template>

<script>
import HelloWorld from "./components/HelloWorld.vue";
//import axios from "axios";
export default {
  name: "App",
  components: {
    HelloWorld,
  },
  created() {
    // axios.get("http://localhost:3000/login").then((res) => {
    //   console.log(res);
    // });
    const webSocket = new WebSocket("ws://localhost:8088");
    webSocket.onopen = () => {
      console.log("连接成功");
    };
    webSocket.onmessage = (msg) => {
      console.log(msg);
    };
    webSocket.onclose = () => {
      console.log("关闭连接");
    };
    setTimeout(() => {
      webSocket.send("hello i am demo.html");
    }, 1000);
  },
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
