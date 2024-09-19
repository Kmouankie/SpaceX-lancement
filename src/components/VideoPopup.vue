<template>
    <div class="popup">
      <iframe :src="`https://www.youtube.com/embed/${video}`" frameborder="0" allowfullscreen></iframe>
    </div>
  </template>
  
  <script>
  export default {
    props: {
      video: String
    }
  }
  </script>