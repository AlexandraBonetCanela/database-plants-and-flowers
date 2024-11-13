<script>
export default {
  name: "SearchBar",
  data(){
    return {
      text: ""
    };
  },
  methods: {
    clear() {
      this.text = '';
    },
    addPlant(){

    }
  }

}
</script>

<template>
  <div class="search-bar">
    <input v-model="text" placeholder="Search plant"/>
    <button class="clear" @click="clear">Clear</button>
    <button class="add" @click="addPlant">Add plant</button>
  </div>

</template>

<style scoped>
.search-bar {
  display: flex;
  justify-content: space-between;
  align-items: center;
  padding: 10px 20px;
  background-color: #f5f5f5;
  border-bottom: 1px solid #e5e5e5;
}
.search-bar input {
  width: 100%;
  padding: 10px;
  border: 1px solid #e5e5e5;
  border-radius: 4px;
  outline: none;
}
.search-bar button {
  padding: 10px;
  border: 1px solid #e5e5e5;
  border-radius: 4px;
  outline: none;
  cursor: pointer;
  min-width: 100px;
}
.search-bar .clear {
  margin-right: 10px;
}
.search-bar .add {
  background-color: #007bff;
  color: #fff;
}
</style>