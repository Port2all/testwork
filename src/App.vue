<template>
  <div id="app">
    <div id="nav">
      <h1>Dropbox viewer</h1>
    </div>
    <router-view/>
  </div>
</template>

<script>
  // @ is an alias to /src
  import dropboxViewer from '@/components/dropboxViewer.vue'

  export default {
    name: 'home',
    components: {
      dropboxViewer
    }
  }
</script>


<style scoped>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}

  h1{
    text-align:center;
  }
</style>
