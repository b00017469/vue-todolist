<template>
  <input type='text' v-model='text' @keyup.enter='addItemHandler'/>
  <button @click='addItemHandler'>
    +
  </button>
</template>

<script>
export default {
  name: 'AddItemForm',
  data() {
    return {
      text: '',
    };
  },
  methods: {
    addItemHandler() {
      this.$emit('addItem', this.text);
      this.text = '';
    },
  },
};
</script>

<style scoped>

</style>