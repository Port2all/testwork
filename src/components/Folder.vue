<template>
    <tr class="folder" @click="onFolderClick">
        <td>Folder</td>
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
                console.log('doshlo' + this.$route.path + name);
            }
        },
        created() {

        }
    }



</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.folder{background-color:yellow;}
</style>
