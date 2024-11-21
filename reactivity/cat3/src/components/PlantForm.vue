// plant form in a modal
<template>
  <div class="plant-form">
    <form class="plant-form__form">
      <div class="plant-form__form-group">
        <label for="name">Name</label>
        <input type="text" id="name" />
      </div>
      <div class="plant-form__form-group">
        <label for="description">Description</label>
        <textarea id="description"></textarea>
      </div>
      <div class="plant-form__form-group">
        <label for="image">Image URL</label>
        <input type="text" id="image" />
      </div>
      <div class="plant-form__form-group">
        <label for="date">Date</label>
        <input type="date" id="date" />
      </div>
      <div class="plant-form__form-group">
        <label for="family">Family</label>
        <input type="text" id="family" />
      </div>
      <div class="plant-form__form-group">
        <label for="genus">Genus</label>
        <input type="text" id="genus" />
      </div>
      <div class="plant-form__form-group">
        <label for="species">Species</label>
        <input type="text" id="species" />
      </div>
      <div class="plant-form__form-group">
        <label for="labels">Labels</label>
        <input type="text" id="labels" />
      </div>
      <div class="plant-form__form-group">
        <label for="favorite">Favorite</label>
        <input type="checkbox" id="favorite" />
      </div>
      <div class="plant-form__form-group">
        <label for="rating">Rating</label>
        <input type="range" id="rating" min="0" max="5" step="1" />
      </div>
      <div class="plant-form__form-group">
        <label for="personalNote">Personal Note</label>
        <textarea id="personalNote"></textarea>
      </div>
      <div class="plant-form__form-group plant-form__form-group--actions">
        <button type="submit" class="plant-form__submit">Add plant</button>
      </div>
    </form>
  </div>
</template>

<script></script>
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
