<template>
  <header>
    <!-- parte a sinistra con logo -->
    <h1>BOOLFLIX</h1>

    <!-- parte a destra con ricerca -->
    <div class="search">
      <input
        type="text"
        placeholder="Cerca un Film o una SerieTV"
        v-model="userSearch"
        @keyup.enter="$emit('searchVideo', userSearch)"
      />
      <button @click="$emit('searchVideo', userSearch)">CERCA</button>
    </div>
  </header>
</template>

<script>
export default {
  name: "HeaderComp",
  data() {
    return {
      userSearch: "",
    };
  },
};
</script>

<style scoped lang="scss">
header {
  height: 100px;
  background-color: black;
  display: flex;
  justify-content: space-between;
  align-items: center;
  padding: 20px 30px;
  h1 {
    color: red;
    font-size: 3rem;
  }
  .search {
    display: flex;
    width: 25%;
    * {
      font-size: 1rem;
      line-height: 2rem;
      padding: 5px 20px;
      border: none;
    }
    input {
      width: 100%;
    }
    button {
      font-weight: bold;
      border: 2px solid red;
      background-color: transparent;
      color: red;
      transition: all 0.1s ease;
      cursor: pointer;
      &:active {
        background-color: red;
        color: white;
      }
    }
  }
}
</style>
