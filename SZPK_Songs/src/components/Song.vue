<template>
    <tr>
        <th scope="row">{{ song.TITLE }}</th>
        <td>{{ song.YEAR }}</td>
        <td>{{ song.TIME }}</td>
        <td>{{ song.BPM }}</td>
        <td>{{ song.GENRE }}</td>
    </tr>
</template>

<script setup>
    var props = defineProps(['song']);

</script>

<style>

</style>

