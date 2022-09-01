<template>
  <div id="app">
    <Gallery :dataGallery="this.dataGallery"/>
  </div>
</template>

<script>
import Gallery from './components/Gallery.vue'
import axios from 'axios'
export default {
  name: 'App',
  return:{
    dataGallery:null
  },
  components: {
    Gallery
  },
  mounted() {
    this.getData();
  },
  methods: {
    getData() {
        axios.get('https://jsonplaceholder.typicode.com/albums/1/photos')
        .then (response => {
            this.dataGallery = response.data                       
        })
        .catch (e=>console.log(e))
    }
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
