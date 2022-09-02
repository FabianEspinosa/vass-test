<template>
  <div id="app">
    <Gallery :data="dataGallery" v-if = "dataGallery.length > 0"/>
  </div>
</template>

<script>
import Gallery from './components/Gallery.vue'
import axios from 'axios'
export default {
  name: 'App',
  data() {
    return {
        dataGallery:[]
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
