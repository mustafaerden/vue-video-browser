<template>
  <div class="search-bar">
    <!--<input type="text" v-on:input="onInput" />-->
    <input type="text" @input="onInput" />
  </div>
</template>

<script>
export default {
  name: "SearchBar",
  methods: {
    // child comp tan parent comp a data göndermek emit ile oluyor;
    onInput(e) {
      this.$emit("termChange", e.target.value);
    }
  }
};
</script>

<style scoped>
.search-bar {
  text-align: center;
  margin: 20px;
}
input {
  width: 75%;
}
</style>