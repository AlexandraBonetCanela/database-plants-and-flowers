<template>
  <header class="header">
    <div class="header__left">
      <img class="logo" src="./assets/uoc-logo.png" alt="UOC logo" />
      <h1 class="title">Plants Book</h1>
    </div>
  </header>
  <SearchBar v-on:show-form="toggleForm" v-on:search="setSearchTerm" />
  <FilterBar
    v-on:sort-items="sortPlants"
    v-on:order-items="orderPlants"
    v-on:favourite-items="favouritePlants"
  />
  <main class="main">
    <PlantList :plants="plantsFiltered" v-on:delete-plant="deletePlant" />
  </main>
  <ModalLayer v-if="showModal" v-on:closeModal="toggleForm">
    <template v-slot:header>
      <h2>Add a new Plant</h2>
    </template>
    <template v-slot:body>
      <PlantForm v-on:add-plant="addPlant" />
    </template>
  </ModalLayer>
</template>

<script>
import FilterBar from "./components/FilterBar.vue";
import ModalLayer from "./components/ModalLayer.vue";
import PlantForm from "./components/PlantForm.vue";
import PlantList from "./components/PlantList.vue";
import SearchBar from "./components/SearchBar.vue";

export default {
  name: "App",
  components: {
    SearchBar,
    PlantList,
    FilterBar,
    PlantForm,
    ModalLayer,
  },
  data() {
    return {
      showModal: false,
      sortBy: "name",
      orderBy: "asc",
      favoriteOnly: false,
      searchTerm: "",
      plantList: [
        {
          id: "1",
          name: "Monstera",
          description:
            "The Monstera is a tropical plant native to Central America. It is known for its large, glossy leaves that have natural holes in them. The Monstera is a popular houseplant due to its unique appearance and low maintenance requirements.",
          image:
            "https://www.flowerdaise.com.au/wp-content/uploads/2021/02/0174-scaled.jpg",
          date: "2021-06-01",
          family: "Araceae",
          genus: "Monstera",
          species: "Monstera deliciosa",
          labels: ["tropical", "houseplant", "low maintenance"],
          favorite: true,
          rating: 5,
          personalNote: "This is my favorite plant",
        },
        {
          id: "2",
          name: "Fiddle Leaf Fig",
          description:
            "The Fiddle Leaf Fig is a popular houseplant known for its large, violin-shaped leaves. It is native to western Africa and is part of the Ficus genus. The Fiddle Leaf Fig is a favorite among interior designers due to its striking appearance and ability to grow indoors.",
          image:
            "https://www.flowerdaise.com.au/wp-content/uploads/2021/02/0185-scaled.jpg",
          date: "2021-06-01",
          family: "Moraceae",
          genus: "Ficus",
          species: "Ficus lyrata",
          labels: ["houseplant", "interior", "low maintenance"],
          favorite: false,
          rating: 4,
          personalNote: "I like this plant",
        },
        {
          id: "3",
          name: "Snake Plant",
          description:
            "The Snake Plant, also known as Mother-in-Law's Tongue, is a popular houseplant known for its upright, sword-shaped leaves. It is native to West Africa and is part of the Asparagaceae family. The Snake Plant is a hardy plant that can survive in low light and with infrequent watering.",
          image:
            "https://www.flowerdaise.com.au/wp-content/uploads/2021/02/0181-scaled.jpg",
          date: "2021-06-01",
          family: "Asparagaceae",
          genus: "Sansevieria",
          species: "Sansevieria trifasciata",
          labels: ["houseplant", "low light", "low maintenance"],
          favorite: false,
          rating: 3,
          personalNote: "I don't like this plant",
        },
        {
          id: "4",
          name: "Pothos",
          description:
            "The Pothos plant, also known as Devil's Ivy, is a popular houseplant known for its heart-shaped leaves and trailing vines. It is native to the Solomon Islands and is part of the Araceae family. The Pothos is a versatile plant that can thrive in a variety of conditions.",
          image:
            "https://www.flowerdaise.com.au/wp-content/uploads/2021/02/0181-scaled.jpg",
          date: "2021-06-01",
          family: "Araceae",
          genus: "Epipremnum",
          species: "Epipremnum aureum",
          labels: ["houseplant", "trailing", "low maintenance"],
          favorite: true,
          rating: 5,
          personalNote: "This is my favorite plant",
        },
        {
          id: "5",
          name: "ZZ Plant",
          description:
            "The ZZ Plant, also known as Zanzibar Gem, is a popular houseplant known for its glossy, dark green leaves. It is native to eastern Africa and is part of the Araceae family. The ZZ Plant is a hardy plant that can survive in low light and with infrequent watering.",
          image:
            "https://www.flowerdaise.com.au/wp-content/uploads/2021/02/0181-scaled.jpg",
          date: "2021-06-01",
          family: "Araceae",
          genus: "Zamioculcas",
          species: "Zamioculcas zamiifolia",
          labels: ["houseplant", "low light", "low maintenance"],
          favorite: false,
          rating: 4,
          personalNote: "I like this plant",
        },
      ],
    };
  },
  methods: {
    deletePlant(id) {
      this.plantList = this.plantList.filter((plant) => plant.id !== id);
    },
    toggleForm() {
      this.showModal = !this.showModal;
    },
    setSearchTerm(term) {
      this.searchTerm = term;
    },
    addPlant(plant) {
      this.plantList = [...this.plantList, plant];
      this.showModal = false;
    },
    sortPlants(sortBy) {
      this.sortBy = sortBy;
    },
    orderPlants(orderBy) {
      this.orderBy = orderBy;
    },
    favouritePlants(favoriteOnly) {
      this.favoriteOnly = favoriteOnly;
    },
  },
  computed: {
    plantsFiltered() {
      let plantList = [...this.plantList];

      plantList.sort((a, b) => {
        if (this.sortBy === "name") {
          if (this.orderBy === "asc") {
            return a.name.localeCompare(b.name);
          } else {
            return b.name.localeCompare(a.name);
          }
        } else if (this.sortBy === "date") {
          if (this.orderBy === "asc") {
            return a.date.localeCompare(b.date);
          } else {
            return b.date.localeCompare(a.date);
          }
        } else if (this.sortBy === "family") {
          if (this.orderBy === "asc") {
            return a.family.localeCompare(b.family);
          } else {
            return b.family.localeCompare(a.family);
          }
        } else if (this.sortBy === "rating") {
          if (this.orderBy === "asc") {
            return a.rating - b.rating;
          } else {
            return b.rating - a.rating;
          }
        }
      });

      if (this.favoriteOnly) {
        plantList = plantList.filter((plant) => plant.favorite);
      }

      if (!this.searchTerm) {
        return plantList;
      } else {
        plantList = plantList.filter((plant) => {
          return (
            plant.name.toLowerCase().includes(this.searchTerm.toLowerCase()) ||
            plant.description
              .toLowerCase()
              .includes(this.searchTerm.toLowerCase()) ||
            plant.labels.some((item) =>
              item.toLowerCase().includes(this.searchTerm.toLowerCase())
            )
          );
        });
      }
      return plantList;
    },
  },
};
</script>

<style>
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
