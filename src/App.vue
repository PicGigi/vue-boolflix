<template>
  <div>
    <header-page @queryChange="search"/>
    <main-page :arr-movies="arrMovies" :arrTv="arrTv"/>
  </div>
</template>

<script>
import axios from 'axios';
import HeaderPage from '@/components/HeaderPage.vue';
import MainPage from '@/components/MainPage.vue';

export default {
  name: 'App',
  components: {
    HeaderPage,
    MainPage,
  },
  data() {
    return {
      baseApiUrl: 'https://api.themoviedb.org/3',
      apiKey: '9b7c9bfcf908fb76fe43f27b944e327d',
      resultsLanguage: 'it-IT',
      arrMovies: [],
      arrTv: [],
    };
  },
  methods: {
    search(queryString) {
      axios.get(`${this.baseApiUrl}/search/movie`, {
        params: {
          api_key: this.apiKey,
          language: this.resultsLanguage,
          query: queryString,
        },
      })
        .then((responseAxios) => {
          this.arrMovies = responseAxios.data.results;
          console.log(this.arrMovies);
        });

      axios.get(`${this.baseApiUrl}/search/tv`, {
        params: {
          api_key: this.apiKey,
          language: this.resultsLanguage,
          query: queryString,
        },
      })
        .then((responseAxios) => {
          this.arrTv = responseAxios.data.results;
          console.log(this.arrTv);
        });
    },
  },
};

</script>

<style lang="scss">
*{
  margin: 0;
  padding: 0;
  box-sizing: border-box;
  font-family: 'Segoe UI', Roboto;
}
</style>
