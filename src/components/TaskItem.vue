<template>
  <div>
    <input type='checkbox' checked='{{isDone}}'/>
    <label>{{title}}</label>
    <button @click="$emit('removeItem', id)">Delete</button>
  </div>
</template>

<script>
export default {
  name: 'TaskItem',
  props: {
    title: String,
    isDone: Boolean,
    id: String,
  },
  data(){
    return{

    }
  }

};
</script>

<style scoped>

</style>