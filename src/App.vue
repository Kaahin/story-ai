<template>
  <div class="content">
    <h1>Storytelling By GPT-3 Powered By OpenAI API</h1>
    <h3>"Tell me how it starts and i will tell u how it ends" - GPT-3</h3>
    <div class="view">
      <GP3 @result="getResult"/>
      <div class="output-view">{{textOut}}</div>
    </div>
  </div>
</template>

<script setup>
import GP3 from "./components/GP3.vue";
import { ref } from "vue";

let textOut= ref(null);
const getResult = (data) => {
  textOut.value = data;
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
.output-view {
  border: 1px solid black;
  width: 300px;
  height: 400px;
}
.view {
  display: flex;
  flex-direction: row;
  justify-content: space-around;
  align-items: center;
  width: 1000px;
  height: 600px;
}
.content {
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-content: center;
  position: relative;
  width: 1000px;
}
</style>
