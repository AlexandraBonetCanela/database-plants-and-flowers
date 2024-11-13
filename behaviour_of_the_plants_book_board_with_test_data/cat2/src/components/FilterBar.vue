<script>
export default {
  name: "FilterBar",
  data(){
    return{
      selectedSortBy: 'name',
      selectedSortedOrder: 'asc',
      showOnlyFavorites: false
    };
  }
}
</script>

<template>
  <div class="filter-bar">
    <div class="filter-bar__select">
      <label for="sortBy">Sort by</label>
      <select v-model="selectedSortBy" id="sortBy">
        <option value="name">Name</option>
        <option value="date">Date</option>
        <option value="family">Family</option>
        <option value="rating">Rating</option>
      </select>
    </div>

    <div class="filter-bar__select">
      <label for="orderBy">Order by</label>
      <select v-model="selectedSortedOrder" id="orderBy">
        <option value="asc">Ascending</option>
        <option value="desc">Descending</option>
      </select>
    </div>

    <div class="filter-bar__check">
      <label for="favoritesOnly">Show only favorites</label>
      <input type="checkbox" v-model="showOnlyFavorites" id="favoritesOnly" >
    </div>
  </div>
</template>

<style scoped>
filter-bar {
  display: flex;
  align-items: center;
  padding: 20px;
  background-color: #f5f5f5;
  border-bottom: 1px solid #ccc;
}
.filter-bar__select {
  display: flex;
  align-items: center;
  margin-right: 20px;
}
.filter-bar__select label {
  margin-right: 10px;
}
.filter-bar__select select {
  padding: 10px;
  border: 1px solid #ccc;
  border-radius: 4px;
  outline: none;
}
.filter-bar__check {
  display: flex;
  align-items: center;
}
.filter-bar__check input {
  margin-right: 10px;
}
.filter-bar__check label {
  cursor: pointer;
}
</style>