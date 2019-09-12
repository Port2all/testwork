<template>
    <div class="dropboxViewer container">
        <h1>{{ '/' + this.path }}</h1>

        <table class="table table-striped">
            <thead>
            <tr>
                <th scope="col">Type</th>
                <th scope="col">Name</th>
                <th scope="col">Size</th>
                <th scope="col">Last modified</th>
            </tr>
            </thead>
            <tbody>
            <component :is="item['.tag']"
                       v-for="item in folderList"
                       :name="item.name"
                       :size="item.size"
                       :date="item.server_modified">

            </component>
            </tbody>
        </table>


    </div>
</template>

<script>
    import File from '@/components/File.vue';
    import Folder from '@/components/Folder.vue';

    export default {
        name: 'dropboxViewer',
        components:{
          'file': File,
          'folder': Folder
        },
        props: {
            msg: String,
            folderList: Array,
            path: String,
        },
        data() {
            return{

            }
        },
        created() {
            console.log('aaa' + path); //2222
        }
    }





</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
    h3 {
        margin: 40px 0 0;
    }
    ul {
        list-style-type: none;
        padding: 0;
    }
    li {
        display: inline-block;
        margin: 0 10px;
    }
    a {
        color: #42b983;
    }
</style>
