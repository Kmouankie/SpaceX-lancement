<template>
  <div class="app-container">
    <Header class="header" />
    <NextLaunch class="next-launch" :nextLaunch="nextLaunch" />
    <LaunchFilter class="launch-filter" v-model="filter" />
    <LaunchList class="launch-list" :launches="launches" :filter="filter" />
  </div>
</template>

<script>
import Header from './components/Header.vue';
import NextLaunch from './components/NextLaunch.vue';
import LaunchFilter from './components/LaunchFilter.vue';
import LaunchList from './components/LaunchList.vue';
import LaunchpadImages from './components/LaunchpadImages.vue'

export default {
  components: { Header, NextLaunch, LaunchFilter, LaunchList ,LaunchpadImages},
  data() {
    return {
      nextLaunch: {},
      launches: [],
      filter: 'all'
    }
  },
  async mounted() {
    const response = await fetch('https://api.spaceXdata.com/v4/launches');
    const data = await response.json();
    console.log('API response:', data);
    this.launches = data;
    this.nextLaunch = data[0];
  }
}
</script>

<style src="./styles.css"></style>