<template>
    <tr class="file">
        <td>File</td>
        <td>{{ name }}</td>
        <td>{{ formatBytes(size) }}</td>
        <td>{{ formatDate(new Date(date)) }}</td>
    </tr>
</template>

<script>


    export default {
        name: 'File',
        props: {
            name: String,
            size: Number,
            date: String,
        },
        methods: {
             formatBytes(bytes, decimals = 2) {
                if (bytes === 0) return '0 Bytes';

                const k = 1024;
                const dm = decimals < 0 ? 0 : decimals;
                const sizes = ['Bytes', 'KB', 'MB', 'GB', 'TB', 'PB', 'EB', 'ZB', 'YB'];

                const i = Math.floor(Math.log(bytes) / Math.log(k));

                return parseFloat((bytes / Math.pow(k, i)).toFixed(dm)) + ' ' + sizes[i];
            },
            formatDate(value) {
                let time = new Date(value);

                let diff = new Date() - value; // разница в миллисекундах

                if (diff < 1000) { // меньше 1 минуты
                    return 'right now';
                }

                let sec = Math.floor(diff / 1000); // преобразовать разницу в секунды

                if (sec < 60) {
                    return sec + ' sec. ago';
                }

                let min = Math.floor(diff / 60000); // преобразовать разницу в минуты
                if (min < 60) {
                    return min + ' min. ago';
                }

                // отформатировать дату
                // добавить ведущие нули к единственной цифре дню/месяцу/часам/минутам
                let d = value;
                d = [
                    '0' + d.getDate(),
                    '0' + (d.getMonth() + 1),
                    '' + d.getFullYear(),
                    '0' + d.getHours(),
                    '0' + d.getMinutes()
                ].map(component => component.slice(-2)); // взять последние 2 цифры из каждой компоненты

                // соединить компоненты в дату
                return d.slice(0, 3).join('.') + ' ' + d.slice(3).join(':');
            }
        },
        created(){

        }

    }



</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>

</style>
