<template>
  <div class="plant-list">
    <PlantItem
      v-for="plant in plants"
      :plant="plant"
      v-on:delete-plant="deletePlant"
    />
  </div>
</template>

<script>
import PlantItem from "./PlantItem.vue";
export default {
  name: "PlantList",
  components: {
    PlantItem,
  },
  props: {
    plants: {
      type: Array,
      required: true,
    },
  },
  methods: {
    deletePlant(id) {
      this.$emit("delete-plant", id);
    },
  },
};
</script>

<style>
.plant-list {
  padding: 20px;
  display: grid;
  grid-template-columns: repeat(2, 1fr);
  grid-gap: 20px;
}
</style>
