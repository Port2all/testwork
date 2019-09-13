<template>
    <div class="dropboxViewer container">
        <h1>{{ this.path }}</h1>

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
            folderList: Array,
            path: String,
        },
        data() {
            return{

            }
        },
        created() {

        }
    }





</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style>
td, th{
    text-align:left;
}
h1{
    text-align:left;
}
</style>
