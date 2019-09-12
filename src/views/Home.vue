<template>
  <div class="home">
    <img alt="Vue logo" src="../assets/logo.png">
    <dropboxViewer v-bind:folderList="folderList" />
    {{ getFolderFromPath(path) }}

  </div>
</template>

<script>
// @ is an alias to /src
import dropboxViewer from '@/components/dropboxViewer.vue'
import {Dropbox} from "dropbox";

let dbx = new Dropbox({accessToken: 'zRQCPz88YEAAAAAAAAAAEdOAeIFUECs2_TX41zjv8lgxiSuS5qTG2dSBwgoczc6v'});


export default {
  name: 'home',
  components: {
    dropboxViewer
  },
  props: {
    path: String,
  },
  methods: {
          getFolderFromPath(path){
             if(path !== ''){
            dbx.filesListFolder({path: '/' + path})
                    .then(response => {
                      this.folderList = response.entries;
                      console.log(folderList);
                    })
                    .catch(error => {
                      console.log(error);
                    });
              }
               else{
        dbx.filesListFolder({path: ''})
                .then(response => {
                  this.folderList = response.entries;
                  console.log(folderList);
                })
                .catch(error => {
                  console.log(error);
                });
      }
          }
  },
  data() {
    return {
      folderList: [],
    }
  },
  created() {
console.log(this.path);
  }
}



</script>
