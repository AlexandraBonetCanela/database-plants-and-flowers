<script>
export default {
  name: "FilterBar"
}
</script>

<template>

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