<template>
    <section>
      <h2>Prochain lancement</h2>
      <p>Date: {{ nextLaunch.date }}</p>
      <p>Nom: {{ nextLaunch.name }}</p>
      <p>Décompte: {{ countdown }}</p>
    </section>
  </template>
  
  <script>
  import moment from 'moment';
  export default {
    props: {
      nextLaunch: Object
    },
    computed: {
      countdown() {
        const launchDate = moment(this.nextLaunch.date);
      const now = moment();
      const diff = launchDate.diff(now);

      const days = Math.floor(diff / (1000 * 60 * 60 * 24));
      const hours = Math.floor((diff % (1000 * 60 * 60 * 24)) / (1000 * 60 * 60));
      const minutes = Math.floor((diff % (1000 * 60 * 60)) / (1000 * 60));
      const seconds = Math.floor((diff % (1000 * 60)) / 1000);
      //console.log('countdown:', `${days} jours, ${hours} heures, ${minutes} minutes, ${seconds} secondes`); 
      return `${days} jours, ${hours} heures, ${minutes} minutes, ${seconds} secondes`;
      }
    }
  }
  </script>