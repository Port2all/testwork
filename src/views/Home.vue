<template>
  <div class="home">
    <div v-if="loading" id="loading">
      <img src="../assets/loading.gif">
    </div>
    <img alt="Vue logo" src="../assets/logo.png">

    <dropboxViewer v-bind:folderList="folderList" v-bind:path="$route.path" />


  </div>
</template>

<script>
// @ is an alias to /src
import dropboxViewer from '@/components/dropboxViewer.vue'
import {Dropbox} from "dropbox";



export default {
  name: 'home',
  components: {
    dropboxViewer
  },
  props: {

  },
  data() {
    return {
      folderList: [],
      loading: false,
    }
  },
  created() {
    this.getFolderFromPath(this.$route.path)
  },
  beforeRouteUpdate(to, from, next) {
    this.getFolderFromPath(to.path);
    next()
  },
  methods: {
          getFolderFromPath(path){
            let dbx = new Dropbox({accessToken: 'zRQCPz88YEAAAAAAAAAAEdOAeIFUECs2_TX41zjv8lgxiSuS5qTG2dSBwgoczc6v'});
            path = path.trim();
            path = path === '/' ? '' : path;
            this.loading = true;
            dbx.filesListFolder({path: path})
                    .then(response => {
                      this.folderList = response.entries;
                      console.log(response.entries)
                      this.loading = false;
                    })
                    .catch(error => {
                      console.log(error);
                    });


          }
  }

}


</script>

<style>
  h1{
    text-align:center;
  }

  #loading{
    position: fixed;
    top:0;
    left: 0;
    z-index:5;
    width: 100%;
    height: 100%;
    background: black;
    opacity: 0.5;
    padding-top: 20%;
  }
</style>
