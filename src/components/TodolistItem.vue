<template>
  <div class='wrapper'>
    <label>{{ todolist.title }}</label>
    <button @click="$emit('removeItem', todolist.id)">Delete</button>
    <AddItemForm @addItem='createTask'/>
    <div v-if='!!tasks'>
      <TaskItem v-for='task in tasks'
                :task='task'
                :key='task.id'
      />
    </div>
  </div>
</template>

<script>
import TaskItem from './TaskItem.vue';
import AddItemForm from './AddItemForm.vue';

export default {
  name: 'TodolistItem',
  components: { AddItemForm, TaskItem },
  props: {
    todolist: {},
    tasks: {},
  },
  data() {
    return {};
  },
  methods:{
    createTask(title){
      this.$emit('addTask', title, this.todolist.id)
    }
  }

};
</script>

<style scoped>
.wrapper {
  border: 1px solid white;
}
</style>