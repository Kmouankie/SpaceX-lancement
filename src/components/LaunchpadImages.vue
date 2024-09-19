<template>
    <div>
      <img v-for="(image, index) in images" :key="index" :src="image" alt="Launchpad image">
    </div>
  </template>
  
  <script>
  export default {
    data() {
      return {
        images: []
      }
    },
    mounted() {
      fetch('https://api.spacexdata.com/v4/launchpads')
        .then(response => response.json())
        .then(data => {
          this.images = data.map(item => item.images.large[0]);
        });
    }
  }
  </script>
  
  <style scoped>
  img {
    width: 200px;
    height: 200px;
    margin: 10px;
  }
  </style>