<template>
    <tr class="folder">
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
        }
    }



</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>

</style>
