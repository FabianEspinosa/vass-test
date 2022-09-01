<template>
  <div id="app">
    <Gallery :data="dataGallery"/>
  </div>
</template>

<script>
import Gallery from './components/Gallery.vue'
import axios from 'axios'
export default {
  name: 'App',
  data() {
    return {
        dataGallery:null
    }
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
