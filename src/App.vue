<template>
  <div class="container">
    <Header/>
    <Mission/>
    <Map/>
    <Mission2/>
    <Benifit/>
    <Benifit2/> 
    <Gallery/>
  </div>
</template>

<script lang="ts">
import Benifit from './components/Benifit.vue';
import Benifit2 from './components/Benifit2.vue';
import Gallery from './components/Gallery.vue';
import Header from './components/Header.vue';
import Map from './components/Map.vue';
import Mission from './components/Mission.vue';
import Mission2 from './components/Mission2.vue';
export default {
  components: {
    Header,
    Mission,
    Map,
    Mission2,
    Benifit,
    Benifit2,
    Gallery
}
}
</script>