<script>
export default {
  name: "PlantForm",
  data(){
    return {
      name: "",
      description: "",
      imageURL: "",
      date: null,
      family: "",
      genus: "",
      species: "",
      labels: "",
      favorite: false,
      rating: 3,
      personalNote: ""
    };
  }
}
</script>

<template>
  <div class="plant-form__form">
    <form class="plant-form__form">

      <div class="plant-form__form-group">
        <label for="name">Name</label>
        <input type="text" v-model="name" id="name" name="name" />
      </div>


      <div class="plant-form__form-group">
        <label for="description">Description</label>
        <input type="text" v-model="description" id="description" name="description"/>
      </div>

      <div class="plant-form__form-group">
        <label for="imageURL">Image URL</label>
        <input type="text" v-model="imageURL" id="imageURL" name="imageURL"/>
      </div>

      <div class="plant-form__form-group">
        <label for="date">Date</label>
        <input type="date" v-model="date" id="date" name="date"/>
      </div>

      <div class="plant-form__form-group">
        <label for="family">Family</label>
        <input type="text" v-model="family" id="family" name="family"/>
      </div>

      <div class="plant-form__form-group">
        <label for="genus">Genus</label>
        <input type="text" v-model="genus" id="genus" name="genus"/>
      </div>

      <div class="plant-form__form-group">
        <label for="species">Species</label>
        <input type="text" v-model="species" id="species" name="species"/>
      </div>

      <div class="plant-form__form-group">
        <label for="labels">Labels</label>
        <input type="text" v-model="labels" id="labels" name="labels"/>
      </div>

      <div class="plant-form__form-group">
        <label for="favorite">Favorite</label>
        <input type="checkbox" v-model="favorite" id="favorite" name="favorite"/>
      </div>

      <div class="plant-form__form-group">
        <label for="rating">Rating</label>
        <input type="range" v-model="rating" id="rating" name="rating" min="1" max="5"/>
      </div>

      <div class="plant-form__form-group">
        <label for="personalNote">Personal Note</label>
        <textarea v-model="personalNote" id="personalNote" name="personalNote"></textarea>
      </div>

      <div class="plant-form__form-group plant-form__form-group--actions">
        <button type="submit" class="plant-form__submit" id="submitButton" name="submitButton">Add plant</button>
      </div>
    </form>
  </div>
</template>

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