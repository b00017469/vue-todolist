<template>
  <div>
    <input type='checkbox' v-model='isDone'>
    <EditableSpan :text='task.title' />
    <button>del</button>
  </div>
</template>

<script>
import EditableSpan from './EditableSpan.vue';

export default {
  name: 'TaskItem',
  components: { EditableSpan },
  props: {
    task: {},
  },
  data() {
    return {
      isDone: this.task.isDone,
    };
  },
};
</script>

<style scoped>

</style>