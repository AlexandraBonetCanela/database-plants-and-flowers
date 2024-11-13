<script>

import SearchBar from "@/components/SearchBar.vue";
import FilterBar from "@/components/FilterBar.vue";
import PlantList from "@/components/PlantList.vue";
import ModalLayer from "@/components/ModalLayer.vue";
import PlantForm from "@/components/PlantForm.vue";

import SunFlowerImage from "@/assets/sunflower.jpg";
import RoseFlowerImage from "@/assets/rose.jpg";
import JasmineFlowerImage from "@/assets/jasmine.jpeg";
import LilyFlowerImage from "@/assets/lily.jpg";
import DahliaFlowerImage from "@/assets/dahlia.jpg"

export default {
  name: 'App',
  components: {
    SearchBar,
    FilterBar,
    PlantList,
    ModalLayer,
    PlantForm
  },
  data(){
    return {
      plants: [
        {
          id: 1,
          name: "Rose",
          description: "The Classic",
          image: RoseFlowerImage,
          date: "2024-05-08",
          family: "Rosaceae",
          genus: "Rosa",
          species: "Rosa rubiginosa",
          labels: ["Flower", "Yellow", "Cat friendly"],
          favorite: false,
          rating: 2,
          personalNote: "Had them before and died"
        },
        {
          id: 2,
          name: "Jasmine",
          description: "A beautiful red flower",
          image: JasmineFlowerImage,
          date: "2024-05-10",
          family: "Oleaceae",
          genus: "Jasminum",
          species: "Rosa rubiginosa",
          labels: ["Flower", "White"],
          favorite: true,
          rating: 5,
          personalNote: "Not too bad"
        },
        {
          id: 3,
          name: "Lily",
          description: "Lilium candidum",
          image: LilyFlowerImage,
          date: "2024-05-10",
          family: "Liliaceae",
          genus: "Lilium",
          species: "Rosa rubiginosa",
          labels: ["Flower", "White"],
          favorite: true,
          rating: 4,
          personalNote: "It is a survivor"
        },
        {
          id: 4,
          name: "Dahlia",
          description: "A beautiful red flower",
          image: DahliaFlowerImage,
          date: "2024-05-10",
          family: "Asteraceae",
          genus: "Dahlia",
          species: "Coreopsideae",
          labels: ["Flower", "Pink", "Garden", "Outdoor"],
          favorite: true,
          rating: 5,
          personalNote: "My favorite plant"
        },
        {
          id: 5,
          name: "Sunflower",
          description: "The best for the Garden",
          image: SunFlowerImage,
          date: "2024-05-10",
          family: "Asteraceae",
          genus: "Helianthus",
          species: "H. annuus",
          labels: ["Flower", "Yellow", "Garden", "Outdoor"],
          favorite: false,
          rating: 3,
          personalNote: "Would fit our garden"
        }
      ],
      showModal: false
    };
  }
};
</script>

<template>
  <div>
    <header class="header">
      <img src="@/assets/uoc-logo.png" alt="UOC logo" class="logo">
      <h1 class="title">Plants Book</h1>
    </header>

    <div class="content">
      <SearchBar></SearchBar>
      <FilterBar></FilterBar>
      <PlantList :plants="plants"></PlantList>

      <ModalLayer v-if="showModal">
        <template #header>
          <h2>Add New Plant</h2>
        </template>
        <template #body>
          <PlantForm></PlantForm>
        </template>
      </ModalLayer>
    </div>
  </div>
</template>

<style scoped>
body {
  padding: 0;
  margin: 0;
  font-family: "Avenir", Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}
.header {
    display: flex;
    justify-content: space-between;
    align-items: center;
    padding: 0 20px;
    background-color: #f5f5f5;
    border-bottom: 1px solid #e5e5e5;
  }
.header__left {
  display: flex;
  align-items: center;
}
.logo {
  height: 40px;
  margin-right: 10px;
}
.title {
  font-size: 24px;
  font-weight: 400;
}
</style>
