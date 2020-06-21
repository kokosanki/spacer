<template>
  <div class="Searchwrapper">
      <input id="search"
      name="search" :value="value"
      @input="handleChange"
      :class="{ dark }"
      >
  </div>
</template>

<script>
export default {
  name: 'SearchInput',
  props: {
    value: {
      type: String,
      required: true,
    },
    dark: {
      type: Boolean,
      default: false,
    },
  },
  methods: {
    handleChange(e) {
      this.$emit('input', e.target.value);
    },
  },
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

  .dark {
    color: #000;
    border-bottom: 2px solid black;
  }

  #search {
    width: 300px;
    display: flex;
    flex-direction: column;
    &:focus {
      outline: none;
    }
  }

  input {
    height: 30px;
    border: 0;
    border-bottom: 1px solid #fff;
    background: none;
    text-align: center;
    color: #fff;
  }
</style>
