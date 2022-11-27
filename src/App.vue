<template>
  <div id="app">
    <HeaderComp/>
    <div class="albumContainer">
      <div class="flexThis">
        <AlbumComp v-for="(elem, index) in albums" :key="index" :album="elem" />
      </div>
    </div>
  </div>
</template>

<script>
import HeaderComp from './components/HeaderComp.vue';
import AlbumComp from './components/AlbumComp.vue';

import axios from 'axios';


export default {
  name: 'App',
  components: {
    HeaderComp,
    AlbumComp,


  },


    data(){
      return {
        albums: ''
      }
    },

    mounted(){
      this.getAlbums();
    },

    methods: {
      getAlbums(){
        axios.get('https://flynn.boolean.careers/exercises/api/array/music')
          .then((response)=>{
            this.albums = response.data.response
            
          })
      }
    }
  }

</script>

<style lang="scss">
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  background-color: #1E2D3B;
  height: 100vh;
}

*{
  margin: 0;
  padding: 0;
  box-sizing: border-box;

}

.albumContainer{
  width: 80%;
  margin: auto;
}

.flexThis{
  display: flex;
  flex-wrap: wrap;
  justify-content:center;
  justify-content: space-between;
}

</style>
