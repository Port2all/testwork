<template>
    <div class="dropboxViewer container">
        <h2><a href="/">DropBox</a>{{ $route.path }}</h2>

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
            <tr>
                <td colspan="4" v-if="$route.path !== '/'" @click="back" class="goUp">..</td>
            </tr>
            <component :is="item['.tag']"
                       v-for="item in folderList"
                       :name="item.name"
                       :size="item.size"
                       :date="item.server_modified">
            </component>
            <tr>
                <td colspan="4" v-if="folderList.length === 0" class="error">This folder is empty.</td>
            </tr>
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

        },
        methods: {
            back(){
                const pathArr = this.$route.path.split('/');
                const backPath = pathArr.slice(0, pathArr.length - 1).join('/');
                this.$router.push({
                    path: backPath || '/'
                })
            }
        }
    }





</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style>
tr{
    text-align:left;
}
h2{
    text-align:left;
}
.goUp{
        cursor: pointer;
}
    .error{
        background-color: #f7d4df;
    }
</style>
