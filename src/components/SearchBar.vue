<template>
  <div>
    <input
      type="text"
      @input="onInput"
    >
  </div>
</template>

<script>
  export default {
    name: 'SearchBar',
    methods: {
      onInput(e) {
        this.$emit('termChange', e.target.value)
      }
    }
  }
</script>

<style scoped>
  div {
    margin: 1rem 0;
  }

  input {
    width: 100%;
  }
</style>

