<template>
  <div class="home">
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
    }
  },
  created() {
    this.getFolderFromPath(this.$route.path)
  },
  beforeRouteUpdate(to, from) {
    this.getFolderFromPath(to.path);
  },
  methods: {
          getFolderFromPath(path){
            let dbx = new Dropbox({accessToken: 'zRQCPz88YEAAAAAAAAAAEdOAeIFUECs2_TX41zjv8lgxiSuS5qTG2dSBwgoczc6v'});
            path = path.trim();
            path = path === '/' ? '' : path;
            dbx.filesListFolder({path: path})
                    .then(response => {
                      this.folderList = response.entries;
                    })
                    .catch(error => {
                      console.log(error);
                    });


          }
  }

}


</script>

<style scoped>
  h1{
    text-align:center;
  }
</style>
