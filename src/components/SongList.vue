<template>
    <div>
        <SongItem v-for="song in songs" :key="song.id" :song="song"/>
    </div>
</template>

<script>
import SongItem from './SongItem.vue';

    export default {
    name: "SongList",
    props:["songs"],
    components: { SongItem }
}
</script>

<style scoped>

</style>