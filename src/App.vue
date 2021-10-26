<template>
  <div id="app"><FileTree :node="root" /></div>
</template>

<script>
import FileTree from './components/FileTree.vue';
import data from '../public/static/node_modules.json';

export default {
  name: 'App',
  data() {
    return {
      root: data,
    };
  },
  components: {
    FileTree,
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
