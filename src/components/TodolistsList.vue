<template>
  <div>
    <AddItemForm @addItem='createTodo' />
  </div>
  <todolist-item v-for='todo in todolists'
                 :todolist='todo'
                 :tasks='tasks[todo.id]'
                 :key='todo.id'
                 @remove-item='removeTodo'
                 @addTask='createNewTask' />
</template>

<script>
import TodolistItem from './TodolistItem.vue';
import AddItemForm from './AddItemForm.vue';
import { v1 } from 'uuid';

export default {
  name: 'TodolistsList',
  components: { TodolistItem, AddItemForm },
  data() {
    return {
      todolists: [
        { id: '1', title: 'What to learn', filter: 'all' },
        { id: '2', title: 'What to buy', filter: 'all' },
      ],
      tasks: {
        ['1']: [
          { id: v1(), title: 'HTML&CSS', isDone: true },
          { id: v1(), title: 'JS', isDone: false },
        ],
        ['2']: [
          { id: v1(), title: 'Milk', isDone: false },
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
      const todoId = v1();
      this.todolists.push({ id: todoId, title, filter: 'all' });
      this.tasks = { ...this.tasks, [todoId]: [] };
    },
    createNewTask(title, todoId) {
      this.tasks[todoId] = [...this.tasks[todoId], { id: v1(), title, isDone: false }];
    },
  },
};
</script>

<style scoped>

</style>