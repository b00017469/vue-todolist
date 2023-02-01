<template>
  <div>
    <AddItemForm @addItem='createTodo' />
  </div>
  <TaskItem v-for='todo in todolists'
            :title='todo.title'
            :is-done='true'
            :id='todo.id'
            :key='todo.id'
            @remove-item='removeTodo' />
</template>

<script>
import TaskItem from './TaskItem.vue';
import AddItemForm from './AddItemForm.vue';
import { v1 } from 'uuid';

export default {
  name: 'TodolistsList',
  components: { AddItemForm, TaskItem },
  data() {
    return {
      todolists: [
        { id: '1', title: 'What to learn', filter: 'all' },
        { id: '2', title: 'What to buy', filter: 'all' },
      ],
      tasks: {
        ['1']: [
          { id: v1(), title: 'HTML&CSS', isDone: true },
          { id: v1(), title: 'JS', isDone: true },
        ],
        ['2']: [
          { id: v1(), title: 'Milk', isDone: true },
          { id: v1(), title: 'React Book', isDone: true },
        ],
      },
    };
  },
  methods: {
    removeTodo(id) {
      this.todolists = this.todolists.filter(t => t.id !== id);
    },
    createTodo(title) {
      this.todolists.push({ id: v1(), title, filter: 'all' });
    },
  },
};
</script>

<style scoped>

</style>