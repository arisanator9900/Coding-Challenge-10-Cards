<template>
  <img :src="info" alt=""/>
</template>

<script>
//This is the api call file to get all the images
//it will return the image from the index from the array of data.messages 
import axios from 'axios';

export default {
  props: {
    imageNum: {
      Number,
    }
  },
  data () {
    return {
      info: null
    }
  },
  mounted () {
    axios
      .get('https://dog.ceo/api/breeds/image/random/10')
      .then(response => (this.info = response.data.message[0]))
  }
}
</script>

<style>

</style>