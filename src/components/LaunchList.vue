<template>
  <section>
    <h2>Derniers lancements</h2>
    <ul>
      <li v-for="launch in filteredLaunches" :key="launch.id">
        <h3>{{ launch.name }}</h3>
        <p>Date: {{ launch.date }}</p>
        <p>Texte de détail: {{ launch.details }}</p>
        <img :src="launch.image" alt="Image de la mission">
        <p>Lieu de lancement: {{ launch.launch_site }}</p>
        <p>Chargements envoyés: {{ launch.payloads }}</p>
        <p>Clients: {{ launch.clients }}</p>
        <a :href="launch.article" target="_blank">Article de présentation</a>
        <a @click="showVideo(launch.video)">Vidéo de la mission</a>
        <VideoPopup v-if="showVideo" :video="launch.video" />
      </li>
    </ul>
  </section>
</template>

<script>
export default {
  props: {
    launches: Array
  },
  data() {
    return {
      showVideo: false
    }
  },
  computed: {
    filteredLaunches() {
      if (this.filter === 'all') return this.launches;
      else if (this.filter === 'success') return this.launches.filter(launch => launch.success);
      else return this.launches.filter(launch => !launch.success);
    }
  },
  methods: {
    showVideo(video) {
      this.showVideo = true;
    }
  }
}
</script>
<style>
  .popup {
    position: fixed;
    top: 50%;
    left: 50%;
    transform: translate(-50%, -50%);
    background-color: #fff;
    padding: 20px;
    border: 1px solid #ddd;
    border-radius: 10;
  }
</style>