<template>
<div class="wrapper">
  <h1>Spacer</h1>
  <Claim />
  <SearchInput />
</div>
</template>

<script>
import axios from 'axios';
import debounce from 'lodash.debounce';
import Claim from '@/components/Claim.vue';
import SearchInput from '@/components/SearchInput.vue';

const API = 'https://images-api.nasa.gov';
export default {
  name: 'Search',
  components: { Claim, SearchInput },
  data() {
    return {
      searchValue: '',
      results: [],
    };
  },
  methods: {
    // eslint-disable-next-line
    handleInput: debounce(function() {
      axios.get(`${API}/search?q=${this.searchValue}&media_type=image`)
        .then((response) => {
          console.log(response.data.collection.items);
          this.results = response.data.collection.items;
        })
        .catch((error) => {
          console.log(error);
        });
    }, 500),
  },
};
</script>

<style lang="scss" scoped>
  .wrapper {
    margin: 0;
    padding: 10px;
    width: 100%;
    height: 100vh;
    display: flex;
    flex-direction: column;
    align-items: center;
    background: none;
    background-image: url('../../assets/hero.jpg');
    background-repeat: no-repeat;
    background-size: cover;
    background-position: 50% 0%;
    color: #fff;
  }
</style>
