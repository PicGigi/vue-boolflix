<template>
  <header>
    <h1>BOOLFLIX</h1>
    <form @submit.prevent="$emit('queryChange', queryString)">
      <label for="user-input">
        <input
          type="text"
          name="user-input"
          id="user-input"
          v-model="queryString"
          >
      </label>
      <button>Cerca</button>
  </form>
  </header>
</template>

<script>
export default {
  name: 'HeaderPage',
  data() {
    return {
      queryString: '',
    };
  },
};
</script>

<style lang="scss" scoped>
h1{
  color: red;
}
header{
  height: 10vh;
  background-color: black;
  display: flex;
  align-items: center;
  padding: 1rem;
  gap: 2rem;
  input{
    width: 15rem;
  }
}
</style>
