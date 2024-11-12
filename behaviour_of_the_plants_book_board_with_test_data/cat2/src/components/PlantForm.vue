<script>
export default {
  name: "PlantForm"
}
</script>

<template>

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