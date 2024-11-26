<template>
  <div class="plant-item" :class="plant.favorite && 'plant-item--favourite'">
    <button class="plant-item__delete" @click="deletePlant(plant.id)">
      <img src="../assets/delete-button.svg" alt="Delete book" />
    </button>
    <div class="plant-item__image">
      <img :src="plant.image" alt="Plant image" />
    </div>
    <div class="book-item__info">
      <h2 class="plant-item__title">{{ plant.name }}</h2>
      <div class="plant-item__data">
        <p class="plant-item__date"><strong>Date: </strong>{{ plant.date }}</p>
        <p class="plant-item__family">
          <strong>Family: </strong>{{ plant.family }}
        </p>
        <p class="plant-item__genus">
          <strong>Genus: </strong>{{ plant.genus }}
        </p>
        <p class="plant-item__species">
          <strong>Species: </strong>{{ plant.species }}
        </p>
      </div>
      <p class="plant-item__description">{{ plant.description }}</p>
      <p class="plant-item__personal-note">{{ plant.personalNote }}</p>
      <div class="plant-item__extra">
        <p class="plant-item__rating">{{ plant.rating }} / 5</p>
        <p class="plant-item__labels">
          <span v-for="label in plant.labels" :key="label">{{ label }}</span>
        </p>
      </div>
    </div>
  </div>
</template>

<script>
/*

This component must contain a template with the following characteristics:
  - The content will be enclosed by a <div> whose class must be .plant-item
  - The class .plant-item--favorite will be added to this <div> if the post-it passed to it as a prop contains the featured attribute or the featured attribute is true. Being an optional parameter, it will be necessary to manage its inclusion or not depending on whether the parameter is passed or not.
  - Inside .plant-item there will be the following elements:
    - A button with the class .plant-item__delete
      - An <img> element with the src attribute bound to the delete-button.svg image. The alt attribute will be "Delete plant".
    - A <div> with the class .plant-item__image
      - An <img> element with the src attribute bound to the image attribute of the post-it passed as a prop. The alt attribute will be "Plant image".
    - A <div> with the class .plant-item__info. This <div> will contain the following elements:
      - An <h2> element with the class .plant-item__title. The content of this element will be the name attribute of the post-it passed as a prop.
      - A <div> element with the class .plant-item__data. This <div> will contain the following elements:
        - A <p> element with the class .plant-item__date. The content of this element will be "Date: " followed by the date attribute of the post-it passed as a prop.
        - A <p> element with the class .plant-item__family. The content of this element will be "Family: " followed by the family attribute of the post-it passed as a prop.
        - A <p> element with the class .plant-item__genus. The content of this element will be "Genus: " followed by the genus attribute of the post-it passed as a prop.
        - A <p> element with the class .plant-item__species. The content of this element will be "Species: " followed by the species attribute of the post-it passed as a prop.
      - A <p> element with the class .plant-item__description. The content of this element will be the description attribute of the post-it passed as a prop.
      - A <p> element with the class .plant-item__personal-note. The content of this element will be the personalNote attribute of the post-it passed as a prop.
      - A <div> element with the class .plant-item__extra. This <div> will contain the following elements:
        - A <p> element with the class .plant-item__rating. The content of this element will be the rating attribute of the post-it passed as a prop followed by " / 5".
        - A <p> element with the class .plant-item__labels. This <p> will contain the following elements:
          - A <span> element for each label in the labels attribute of the post-it passed as a prop. The content of each <span> will be the label itself.
            

*/

export default {
  name: "PlantItem",
  props: {
    plant: {
      type: Object,
      required: true,
    },
  },
  methods: {
    deletePlant(id) {
      this.$emit("delete-plant", id);
    }

  }
};
</script>

<style>
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
