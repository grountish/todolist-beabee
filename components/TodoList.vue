<template>
  <div class="w-11/12 mx-auto my-5">
    <AddTodo @AddTodo="AddTodo" />
    <div class="text-center border">
      <div class="border flex justify-between">
        <div class="border w-28">Date</div>
        <div class="">Description</div>
        <div class="border w-28">Actions</div>
      </div>
      <div v-for="todo in todos" :key="todo.id">
        <Todo :todo="todo" @DeleteTodo="DeleteTodo" @CheckTodo="CheckTodo" />
      </div>
    </div>
    <Summary :todos="todos" />
   
  </div>
</template>

<script>
export default {
  data() {
    return {
      todos: [],
    }
  },
  methods: {
    AddTodo(todo) {
      this.todos.push(todo)
    },
    DeleteTodo(todoToDelete) {
      let tods = this.todos.filter((todo) => todo.id != todoToDelete.id)

      this.todos = tods
    },
    CheckTodo(todoToCheck) {
      this.todos.forEach((todo) => {
        if (todo.id == todoToCheck.id) {
          todo.check = todoToCheck.check
        }
      })
    }
  }
}
</script>

<style>
</style>