<template>
  <div>
    <form @submit.prevent="addTodos">
      <input type="text" v-model="title" placeholder="Enter the todos..." />
      <input type="submit" value="ADD" />
    </form>
  </div>
</template>

<script lang="ts">
import { Component, Vue, Emit } from "vue-property-decorator";

@Component
export default class AddTodos extends Vue {
  title = "";
  addTodos(): void {
    if (this.title) {
      const newTodo = {
        id: Math.random(),
        title: this.title,
        completed: false,
      };
      this.$emit("add-Todo", newTodo);
      this.title = "";
    }
  }
}
</script>

<style scoped>
form {
  margin-top: 20px;
  display: flex;
}

input[type="text"] {
  flex: 10;
  padding: 5px;
}

input[type="submit"] {
  flex: 2;
}
</style>