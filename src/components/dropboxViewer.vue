<template>
    <div class="dropboxViewer container">
        <h1>{{ msg }}</h1>

        <table class="table table-striped">
            <thead>
            <tr>
                <th scope="col">Type</th>
                <th scope="col">Name</th>
                <th scope="col">Size</th>
                <th scope="col">Creation date</th>
                <th scope="col">Last modified</th>
            </tr>
            </thead>
            <tbody>
            <tr v-for="item in folderList">
                <td>{{ item['.tag'] }}</td>
                <td>{{ item.name }}</td>
                <td>{{ item.size }}</td>
                <td>{{ item.server_modified }}</td>
                <td>{{ item.client_modified }}</td>
            </tr>
            </tbody>
        </table>


    </div>
</template>

<script>

    export default {
        name: 'dropboxViewer',
        data() {
            return{

        }
        },
        props: {
            msg: String,
            folderList: Array
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
