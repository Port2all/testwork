<template>
    <tr class="folder" @click="onFolderClick">
        <td><img src="../assets/folder.png" class="folderIcon">Folder</td>
        <td>{{ name }}</td>
        <td colspan="2"></td>
    </tr>
</template>

<script>

    export default {
        name: 'Folder',
        props: {
            name: String,
        },
        methods: {
            onFolderClick() {
                const currentPath = this.$route.path === '/' ? '' : this.$route.path
              this.$router.push({
                    path: currentPath + '/' + this.name
                });
            }
        },
        created() {

        }
    }



</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.folderIcon{
    width:25px;
}

tr{
    cursor: pointer;
}
tr:hover{
    cursor:pointer;
    background-color: #c8f4f4 !important;
}
</style>
