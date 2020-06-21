<template>
<div :class="[{flexStart: step === 1}, 'wrapper']">
  <h1 :class="[{dark: step === 1}]">Spacer</h1>
  <Claim v-if="step === 0" />
  <SearchInput v-model="searchValue" @input="handleInput"
  :dark="step === 1" />
  <div class="results" v-if="results && !loading && step === 1">
    <Item v-for="item in results" :item="item" :key="item.data[0].nasa" />
</div>
</div>
</template>
<script>
import axios from 'axios';
import debounce from 'lodash.debounce';
import Claim from '@/components/Claim.vue';
import SearchInput from '@/components/SearchInput.vue';
import Item from '@/components/Item.vue';

const API = 'https://images-api.nasa.gov';
export default {
  name: 'Search',
  components: { Claim, SearchInput, Item },
  data() {
    return {
      loading: false,
      step: 0,
      searchValue: '',
      results: [],
    };
  },
  dark: {
    type: Boolean,
    default: false,
  },
  methods: {
    // eslint-disable-next-line
    handleInput: debounce(function() {
      this.loading = true;
      console.log(this.searchValue);
      axios.get(`${API}/search?q=${this.searchValue}&media_type=image`)
        .then((response) => {
          console.log(response.data.collection.items);
          this.results = response.data.collection.items;
          this.loading = false;
          this.step = 1;
        })
        .catch((error) => {
          console.log(error);
        });
    }, 500),
  },
};
</script>

<style lang="scss" scoped>
  h1 {
    font-size: 50px;
  }
  .wrapper {
    margin: 0;
    padding: 20px;
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

    &.flexStart {
      justify-content: flex-start;
      background-image: none;
    }
  }

  .results {
    display: grid;
    grid-template-columns: 1fr;
    grid-gap: 20px;

    @media (min-width: 768px) {
      grid-template-columns: 1fr 1fr 1fr;
    }
  }

  .dark {
    color: #000;
  }
</style>
