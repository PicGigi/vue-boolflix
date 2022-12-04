<template>
  <main>
    <h2 v-if="arrMovies.length">Movies</h2>
    <div class="card-container">
      <flix-card
        v-for="objMovie in arrMovies"
        :key="objMovie.id"
        :title="objMovie.title"
        :original-title="objMovie.original_title"
        :language="objMovie.original_language"
        :score="convertScore(objMovie.vote_average)"
        :img-url="generateUrl(objMovie.poster_path)"
      />
    </div>

    <h2 v-if="arrTv.length">Tv series</h2>
    <div class="card-container">
      <flix-card
        v-for="objTv in arrTv"
        :key="objTv.id"
        :title="objTv.name"
        :original-title="objTv.original_name"
        :language="objTv.original_language"
        :score="convertScore(objTv.vote_average)"
        :img-url="generateUrl(objTv.poster_path)"
      />
    </div>
  </main>
</template>

<script>
import FlixCard from '@/components/FlixCard.vue';

export default {
  name: 'MainPage',
  components: {
    FlixCard,
  },
  props: {
    arrMovies: Array,
    arrTv: Array,
  },
  data() {
    return {
      baseImgUrl: 'https://image.tmdb.org/t/p/',
      imgSize: 'w342',
    };
  },
  methods: {
    generateUrl(path) {
      if (path) {
        return this.baseImgUrl + this.imgSize + path;
      }
      return path;
    },
    convertScore(score) {
      const maxScore = 5;
      const originalMaxScore = 10;
      return {
        score: Math.ceil((score * maxScore) / originalMaxScore),
        maxScore,
      };
    },
  },
};
</script>

<style lang="scss" scoped>
main{
  height: 100%;
  width: 100%;
  min-height: 90vh;
  background-color: darkgray;
  padding: 2rem;

  .card-container{
    display: flex;
    flex-wrap: wrap;
    width: 100%;
  }
}
</style>
