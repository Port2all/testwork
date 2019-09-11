<template>
  <div class="home">
    <img alt="Vue logo" src="../assets/logo.png">
    <HelloWorld msg="DROPBOX EXPLORER"/>
  </div>
</template>

<script>
// @ is an alias to /src
import HelloWorld from '@/components/HelloWorld.vue'

export default {
  name: 'home',
  components: {
    HelloWorld
  }
}

let Dropbox = require('dropbox').Dropbox;
let dbx = new Dropbox({ accessToken: 'zRQCPz88YEAAAAAAAAAAEdOAeIFUECs2_TX41zjv8lgxiSuS5qTG2dSBwgoczc6v' });
dbx.filesListFolder({path: ''})
        .then(function(response) {
          console.log(response);
        })
        .catch(function(error) {
          console.log(error);
        });

</script>
