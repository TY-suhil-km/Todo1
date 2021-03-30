<template>
  <div id="app">
    <Header />
    <AddTodos v-on:add-Todo="addTodo"/>
    <ol>
      <li v-bind:key="todo.id" v-for="todo in todosList">
        <Todos :todos="todo" @deleteTodo="deleteTodo" />
      </li>
    </ol>
    <!-- <Task/> -->
  </div>
</template>

<script lang="ts">
import { Component, Vue, Emit } from "vue-property-decorator";
import HelloWorld from "./components/HelloWorld.vue";
import Todos from "./components/Todos.vue";
import Header from "./components/Header.vue";
import AddTodos from "./components/AddTodos.vue";
import Task from './components/taks/Task.vue'

@Component({
  components: {
    HelloWorld,
    Todos,
    Header,
    AddTodos,
    Task,
  },
})
export default class App extends Vue {
  public todosList: any = [
    {
      id: 1,
      title: "movie",
      completed: false,
    },
    {
      id: 2,
      title: "date",
      completed: true,
    },
    {
      id: 3,
      title: "netflix",
      completed: false,
    },
  ];
  deleteTodo(id: number): void {
    this.todosList = this.todosList.filter((item: any) => item.id != id);
  }
  addTodo(newTodo: object): void{
    this.todosList = [...this.todosList, newTodo]
    // this.todosList.push(newTodo);
  }
}
</script>

<style>

</style>
