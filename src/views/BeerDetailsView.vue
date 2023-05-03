<script setup>
import { ref, onMounted } from 'vue';
import axios from 'axios';
import Footer from '../components/Footer.vue';
import Header from '../components/Header.vue';
import BackgroundBubbles from '../components/BackgroundBubbles.vue';

const beer = ref([]);

const props = defineProps({
  id: {
    type: Number,
    required: true
  }
});

onMounted(async () => {
  const response = await axios.get(
    `https://api.punkapi.com/v2/beers/${props.id}`
  );
  beer.value = response.data[0];
});

</script>

<template>
  
  
  <Header/>

  <div class="main_container">
    <div class="image" :style="{ 'background-image': `url(${beer['image_url']})` }"></div>
    <h1>{{ beer["name"] }}</h1>
    <p>{{ beer["description"] }}</p>
  </div>
  
  <Footer/>
  <BackgroundBubbles/>
  
</template>

<style lang="scss" scoped>

.main_container{
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
  margin-inline: 17%;
  margin-top: 8rem;

  h1{
    font-family: 'Kaushan Script', cursive;
    color: rgb(237, 158, 55);
  }
  
  p{
    font-family: 'Voltaire', cursive;
  }
  
}
.image{
  height: 20rem;
  width: 20rem;
  background-size: contain;
  background-repeat: no-repeat;
  background-position: center;
  z-index: 100;
}
  
</style>


