<script>
export default {
  name: "PlantItem"
}
</script>

<template>

</template>

<style scoped>
.plant-item {
  display: flex;
  padding: 1rem;
  border: 1px solid #ccc;
  border-radius: 0.5rem;
  margin-bottom: 1rem;
  position: relative;
}
.plant-item--favourite {
  background-color: #f0f0f0;
}
.plant-item__delete {
  background-color: transparent;
  border: none;
  padding: 10px;
  cursor: pointer;
  position: absolute;
  top: 0;
  right: 0;
}
.plant-item__delete img {
  width: 20px;
}
.plant-item__image {
  margin-right: 1rem;
}
.plant-item__image img {
  width: 200px;
  height: 200px;
  object-fit: cover;
  border-radius: 0.5rem;
}
.plant-item__info {
  flex: 1;
}
.plant-item__title {
  margin: 0;
  font-size: 1.5rem;
  margin-bottom: 1rem;
  border-bottom: 1px solid #ccc;
}
.plant-item__description {
  margin: 0 0 1rem;
}
.plant-item__data {
  margin-bottom: 1rem;
  border-bottom: 1px solid #ccc;
  padding-bottom: 1rem;
}
.plant-item__data p {
  margin: 0;
}
.plant-item__personal-note {
  margin: 0 0 1rem;
}
.plant-item__extra {
  display: flex;
  justify-content: space-between;
}
.plant-item__rating {
  margin: 0;
}
.plant-item__labels {
  margin: 0;
}
.plant-item__labels span {
  margin-right: 0.5rem;
  padding: 0.25rem 0.5rem;
  border: 1px solid #ccc;
  border-radius: 0.25rem;
  background-color: #f0f0f0;
}
</style>