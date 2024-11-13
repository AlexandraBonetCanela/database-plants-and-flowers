<script>
import PlantItem from "@/components/PlantItem.vue";

export default {
  name: "PlantList",
  components: {PlantItem},
  props: {
    plantList: {
      type: Array,
      required: true
    }
  }
}
</script>

<template>
  <div class="plant-list">
    <plant-item v-for="(plant, index) in plantList" :plant="plant" :key="plant.id"></plant-item>
  </div>
</template>

<style scoped>
.plant-list {
  padding: 20px;
  display: grid;
  grid-template-columns: repeat(2, 1fr);
  grid-gap: 20px;
}
</style>