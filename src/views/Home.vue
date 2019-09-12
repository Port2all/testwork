<template>
  <div class="home">
    <img alt="Vue logo" src="../assets/logo.png">
    <dropboxViewer v-bind:folderList="folderList" />
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
  data() {
    return {
      folderList: [],
    }
  },
  created() {

    let dbx = new Dropbox({accessToken: 'zRQCPz88YEAAAAAAAAAAEdOAeIFUECs2_TX41zjv8lgxiSuS5qTG2dSBwgoczc6v'});
    dbx.filesListFolder({path: ''})
            .then(response => {
              this.folderList = response.entries;
              console.log(response);
            })
            .catch(error => {
              console.log(error);
            });
  }
}



</script>
