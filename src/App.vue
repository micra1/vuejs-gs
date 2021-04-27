<template>
  <img alt="Vue logo" src="./assets/logo.png">
  <!-- <HelloWorld msg="Welcome to Your Vue.js + TypeScript App" byeMsg="Bye suckers!"/> -->
  <RobotBuilder/>
</template>

<script lang="ts">
import { defineComponent } from 'vue'
// import HelloWorld from './home/HelloWorld.vue'
import RobotBuilder from './build/RobotBuilder.vue'

export default defineComponent({
  name: 'App',
  components: {
    RobotBuilder
  }
})
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
