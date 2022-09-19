<template>
  <div>
    <img alt="Vue logo" src="./assets/logo.png" />
    <!-- <HelloWorld msg="Hello, world!!" /> -->
    <LifecycleTest />
    <MyWatchers />
  </div>
</template>

<script>
// import HelloWorld from './components/HelloWorld.vue';
import LifecycleTest from './components/LifecycleTest.vue';
import MyWatchers from './components/MyWatchers.vue';

export default {
  name: 'App',
  components: {
    // HelloWorld,
    LifecycleTest,
    MyWatchers,
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
