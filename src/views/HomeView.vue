<script setup>
import { reactive, toRefs, onBeforeMount, computed } from 'vue';
import Card from '../components/Card.vue';
import SearchBar from '../components/SearchBar.vue';
import BeersService from '../services/BeersService.js';
import ScrollTop from '../components/ScrollTop.vue';
import Footer from '../components/Footer.vue';
import Header from '../components/Header.vue';

const state = reactive({
  beers: [],
  searchQuery: '',
});

const { beers, searchQuery } = toRefs(state);

const beersService = new BeersService();

onBeforeMount(async () => {
  await beersService.fetchAllBeers();
  state.beers = beersService.getBeers();
});

const filteredBeers = computed(() => {

  if (!searchQuery.value) return beers.value

  else return beers.value.filter(beer =>
    beer['name'].toLowerCase().includes(searchQuery.value.toLowerCase())
  )
})

</script>

<template>
  
  <div class="main_container">

    <Header/>

    <SearchBar class="searchbar" v-model="searchQuery" />

    <div class="wrapper">
      <Card v-for="beer in filteredBeers" :beer="beer" :key="beer.id"></Card>
    </div>

  </div>

  <ScrollTop />
  <Footer /> 

</template>

<style lang="scss" scoped>
@import "../assets/scss/Reset.scss";

.main_container {
  display: flex;
  flex-direction: column;
  align-items: center;
  margin-top: 8%;
  width: 100%;
}

.searchbar{
  position: fixed;
  top: 7rem;
  left: -18rem;
  z-index: 110;
  background-color: white;
}
.searchbar:hover{
  cursor: pointer;
}
.searchbar:focus {
  cursor: auto;
  left: 1rem;

}
.wrapper {
  display: flex;
  justify-content: center;
  flex-wrap: wrap;
  gap: 10%; 
}


</style>