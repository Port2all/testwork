<template>
    <tr class="file">
        <td>File</td>
        <td>{{ name }}</td>
        <td>{{ size }}</td>
        <td>{{ date }}</td>
    </tr>
</template>

<script>

    export default {
        name: 'File',
        props: {
            name: String,
            size: Number,
            date: String
        }
    }



</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>

</style>
