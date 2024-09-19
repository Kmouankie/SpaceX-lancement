<template>
    <section>
      <h2>Filtrer les lancements</h2>
      <select v-model="filter">
        <option value="all">Tous les lancements</option>
        <option value="success">Lancements réussis</option>
        <option value="failed">Lancements échoués</option>
      </select>
    </section>
  </template>
  
  <script>
  export default {
    data() {
      return {
        filter: 'all'
      }
    }
  }
  </script>