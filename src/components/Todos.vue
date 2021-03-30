<template>
  <div class="todo-item" v-bind:class="{'is-complete':todos.completed}">
    <h3>
      {{ todos.title.charAt(0).toUpperCase() + todos.title.slice(1) }}
      <input type="checkbox" @change="changeStatus" checked v-if="todos.completed">
      <input type="checkbox" @change="changeStatus"  v-else>
      <button class="del" @click="$emit('deleteTodo', todos.id)">X</button>
    </h3>
  </div>
</template>

<script lang="ts">
import { Component, Prop, Vue } from "vue-property-decorator";
@Component
export default class Todos extends Vue {
  @Prop() private todos: any;
  changeStatus() {
      this.todos.completed = !this.todos.completed;
  }
}
</script>

<style scoped>
.todo-item {
  background: #817474;
  padding: 10px;
  border: none;
  color: aliceblue;
  text-align: center;
  width: 50%;
  align-self: center;
  margin:auto;
   margin-top: 10px;
}

.is-complete {
  text-decoration: line-through;
}

.del {
  background: #ff0000;
  color: #fff;
  border: none;
  padding: 5px 9px;
  border-radius: 50%;
  cursor: pointer;
  float: right;
  margin-right: 20px;
}
</style>
