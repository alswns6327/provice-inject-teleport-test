<template>
    <div :style="song.done ? textStyle.checked : textStyle.unchecked">{{ song.title }}</div>
</template>

<script>
    export default {
        name:"SongItem",
        props:["song"],
        inject:["textStyle"]
    }
</script>

<style scoped>

</style>