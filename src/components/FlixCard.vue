<template>
  <div>
    <ul>
      <li>
        <img v-if="imgUrl"
          :src="imgUrl"
          alt="title"
        >
        <img v-else
          src="@/assets/img/default.jpg"
          alt="title"
        >
        </li>
      <li>{{ title }}</li>
      <li>{{ originalTitle }}</li>
      <li><lang-flag :iso="language" /></li>
      <li>
        <font-awesome-icon
          v-for="i in score.score"
          :key="i"
          icon="fa-solid fa-star"
          :style="{ color: 'yellow' }"
          />
        <font-awesome-icon
          v-for="i in (score.maxScore - score.score)"
          :key="i"
          icon="fa-regular fa-star"
        />
      </li>
    </ul>
  </div>
</template>

<script>
import LangFlag from 'vue-lang-code-flags';

export default {
  name: 'FlixCard',
  components: {
    LangFlag,
  },
  props: {
    title: String,
    originalTitle: String,
    language: String,
    score: Object,
    imgUrl: String,
  },
};
</script>

<style lang="scss" scoped>
ul{
  width: min-content;
  margin: 2rem;
  padding: 1rem;
  border: 2px solid black;
  list-style: none;
}
</style>
