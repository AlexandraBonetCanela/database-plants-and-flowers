// plant form in a modal
<template>
  <div class="plant-form">
    <form class="plant-form__form" @submit.prevent="createPlant">
      <div class="plant-form__form-group">
        <label for="name">Name</label>
        <input type="text" id="name" v-model="name" />
      </div>
      <div class="plant-form__form-group">
        <label for="description">Description</label>
        <textarea id="description" v-model="description"></textarea>
      </div>
      <div class="plant-form__form-group">
        <label for="image">Image URL</label>
        <input type="text" id="image" v-model="image" />
      </div>
      <div class="plant-form__form-group">
        <label for="date">Date</label>
        <input type="date" id="date" v-model="date" test-id="isbn" />
      </div>
      <div class="plant-form__form-group">
        <label for="family">Family</label>
        <input type="text" id="family" v-model="family" />
      </div>
      <div class="plant-form__form-group">
        <label for="genus">Genus</label>
        <input type="text" id="genus" v-model="genus" />
      </div>
      <div class="plant-form__form-group">
        <label for="species">Species</label>
        <input type="text" id="species" v-model="species" />
      </div>
      <div class="plant-form__form-group">
        <label for="labels">Labels</label>
        <input type="text" id="labels" v-model="labels" />
      </div>
      <div class="plant-form__form-group">
        <label for="favorite">Favorite</label>
        <input type="checkbox" id="favorite" v-model="favorite" />
      </div>
      <div class="plant-form__form-group">
        <label for="rating">Rating</label>
        <input
          type="range"
          id="rating"
          min="0"
          max="5"
          step="1"
          v-model="rating"
        />
      </div>
      <div class="plant-form__form-group">
        <label for="personalNote">Personal Note</label>
        <textarea id="personalNote" v-model="personalNote"></textarea>
      </div>
      <div class="plant-form__form-group plant-form__form-group--actions">
        <button type="submit" class="plant-form__submit">Add plant</button>
      </div>
    </form>
  </div>
</template>

<script>
import { uuid } from "vue-uuid";

export default {
  name: "PlantForm",
  data() {
    return {
      id: "",
      name: "",
      description: "",
      image: "",
      date: "",
      family: "",
      genus: "",
      species: "",
      labels: "",
      favorite: false,
      rating: 0,
      personalNote: "",
    };
  },
  methods: {
    resetForm() {
      this.name = "";
      this.description = "";
      this.image = "";
      this.date = "";
      this.family = "";
      this.genus = "";
      this.species = "";
      this.labels = "";
      this.favorite = false;
      this.rating = 0;
      this.personalNote = "";
    },
    createPlant() {
      if (this.name === "" || this.description === "" || this.image === "") {
        alert("Please fill in all required fields");
        return;
      }
      const plant = {
        id: uuid.v4(),
        name: this.name,
        description: this.description,
        image: this.image,
        date: this.date,
        family: this.family,
        genus: this.genus,
        species: this.species,
        labels: this.labels.split(","),
        favorite: this.favorite,
        rating: this.rating,
        personalNote: this.personalNote,
      };
      this.$emit("add-plant", plant);
      this.resetForm();
    },
  },
};
</script>
<style scoped>
.plant-form {
  padding: 1rem;
}
.plant-form__form {
  display: grid;
  grid-template-columns: 1fr 1fr;
  gap: 1rem;
  @media (max-width: 768px) {
    grid-template-columns: 1fr;
  }
}
.plant-form__form-group {
  display: flex;
  flex-direction: column;
}
.plant-form__form-group label {
  margin-bottom: 0.5rem;
}
.plant-form__form-group input,
.plant-form__form-group textarea {
  padding: 0.5rem;
  border: 1px solid #ccc;
  border-radius: 0.25rem;
}
.plant-form__form-group input[type="checkbox"] {
  width: auto;
}
.plant-form__form-group input[type="range"] {
  width: 100%;
}
.plant-form__form-group--actions {
  grid-column: 1 / -1;
}
.plant-form__submit {
  padding: 0.5rem;
  background-color: #007bff;
  color: white;
  border: none;
  border-radius: 0.25rem;
  cursor: pointer;
}
</style>
