<script setup>
import { ref, onMounted } from 'vue';
import axios from 'axios';

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
  <div class="main_container">
    <div class="image" :style="{ 'background-image': `url(${beer['image_url']})` }"></div>
    <h1>{{ beer["name"] }}</h1>
    <p>{{ beer["description"] }}</p>
  </div>
</template>

<style lang="scss" scoped>
.main_container{
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
  margin-inline: 10rem;
  margin-top: 5rem;

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
}
  
</style>


