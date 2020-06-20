<template>
  <div class="Searchwrapper">
      <input class="search"
      name="search" v-model="searchValue" @input="handleInput">
  </div>
</template>

<script>
export default {
  name: 'SearchInput',
};
</script>

<style lang="scss" scoped>
  .Searchwrapper {
    margin: 0;
    padding: 30px;
    width: 100%;
    display: flex;
    flex-direction: column;
    align-items: center;
  }

  .search {
    width: 300px;
    display: flex;
    flex-direction: column;
  }

  input {
    height: 30px;
    border: 0;
    border-bottom: 2px solid black;
    background: none;
    text-align: center;
  }
</style>
