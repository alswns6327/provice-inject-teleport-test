<template>
  <SongList :songs="songs"/>
  <br/><br/>
  <button @click="changeModal">Teleport이용한 모달</button>
  <teleport to="#modal">
    <Modal v-if="isModal"/>
  </teleport>
</template>

<script>
// import { computed } from 'vue';
import { defineAsyncComponent } from 'vue';
import SongList from './components/SongList.vue';
import pMinDelay from 'p-min-delay';
import Loading from './components/Loading.vue';
const Modal = defineAsyncComponent(
    {
        loader : () => pMinDelay(import("./components/Modal.vue"), 5000),
        loadingComponent : Loading,
    }
);

  export default{
    name: "App",
    data() {
        return {
            isModal: false,
            songs: [
                { id: 1, title: "li", done:true },
                { id: 2, title: "li2", done:false },
                { id: 3, title: "li3", done:true },
                { id: 4, title: "li4", done:false},
                { id: 5, title: "li5", done:true},
            ]
        };
    },
    methods : {
        changeModal(){
            this.isModal = !this.isModal;
            setTimeout(()=>{
                this.isModal = !this.isModal
            }, 2000);
        }
    },
    provide() {
        return {
            textStyle: {
                checked: {"text-decoration" : "line-through"},
                unchecked: ""
            },
            // doneCount : computed(()=>{
            //   return this.songs.filter(song => song.done === true).length;
            // })
        };
    },
    components: { SongList, Modal }
}
</script>

<style scoped>
  
</style>
