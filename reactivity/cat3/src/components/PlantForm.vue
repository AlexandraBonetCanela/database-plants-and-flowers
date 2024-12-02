// plant form in a modal
<template>
  <div class="plant-form">
    <form class="plant-form__form" @submit.prevent="createPlant">
      <div v-if="formError" class="error-message">
        Please fill out all required fields: Name, Description, and Image.
      </div>
      <div class="plant-form__form-group">
        <label for="name">Name</label>
        <input v-model="newPlant.name" type="text" id="name" />
      </div>
      <div class="plant-form__form-group">
        <label for="description">Description</label>
        <textarea v-model="newPlant.description" id="description"></textarea>
      </div>
      <div class="plant-form__form-group">
        <label for="image">Image URL</label>
        <input v-model="newPlant.image" type="text" id="image" />
      </div>
      <div class="plant-form__form-group">
        <label for="date">Date</label>
        <input v-model="newPlant.date" type="date" id="date" />
      </div>
      <div class="plant-form__form-group">
        <label for="family">Family</label>
        <input v-model="newPlant.family" type="text" id="family" />
      </div>
      <div class="plant-form__form-group">
        <label for="genus">Genus</label>
        <input v-model="newPlant.genus" type="text" id="genus" />
      </div>
      <div class="plant-form__form-group">
        <label for="species">Species</label>
        <input v-model="newPlant.species" type="text" id="species" />
      </div>
      <div class="plant-form__form-group">
        <label for="labels">Labels</label>
        <input v-model="labels" type="text" id="labels" />
      </div>
      <div class="plant-form__form-group">
        <label for="favorite">Favorite</label>
        <input v-model="newPlant.favorite" type="checkbox" id="favorite" />
      </div>
      <div class="plant-form__form-group">
        <label for="rating">Rating</label>
        <input v-model="newPlant.rating" type="range" id="rating" min="0" max="5" step="1" />
      </div>
      <div class="plant-form__form-group">
        <label for="personalNote">Personal Note</label>
        <textarea v-model="newPlant.personalNote" id="personalNote"></textarea>
      </div>
      <div class="plant-form__form-group plant-form__form-group--actions">
        <button type="submit" class="plant-form__submit">Add plant</button>
      </div>
    </form>
  </div>
</template>

<script>
import { v4 as uuidv4 } from 'uuid';
export default {
  name: "PlantForm",
  data() {
    return {
      newPlant: {
        id: '',
        name: '',
        description: '',
        image: '',
        date: '',
        family: '',
        genus: '',
        species: '',
        labels: [],
        favorite: '',
        rating: '',
        personalNote: '',
      },
      formError: false,
      labels: '',
    };
  },
  methods: {
    createPlant() {
      if (!this.newPlant.name || !this.newPlant.description || !this.newPlant.image) {
        this.formError = true;
        return;
      }
      if(typeof this.labels === 'string'){
        this.newPlant.labels = this.labels.split(',').map(label => label.trim());
      }
      this.newPlant.id = uuidv4();
      this.$emit('create-plant', this.newPlant)
      this.resetForm();
    },
    resetForm(){
      this.newPlant = {
        id: '',
        name: '',
        description: '',
        image: '',
        date: '',
        family: '',
        genus: '',
        species: '',
        labels: [],
        favorite: '',
        rating: '',
        personalNote: '',
      };

      this.formError = false;
      this.labels = '';
    }
  }
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
.error-message {
  color: red;
  background-color: #ffe5e5;
  border: 1px solid red;
  padding: 10px;
  margin-bottom: 10px;
  border-radius: 4px;
  font-size: 14px;
}
</style>
