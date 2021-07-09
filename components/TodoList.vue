<template>
  <div class="w-11/12 mx-auto my-5">
    <AddTodo @AddTodo="AddTodo" />
    <div class="my-3">
      <span>Category to diplay:</span>
      <select name="categories" id="categories" v-model="category">
        <option value="Work">Work</option>
        <option value="Holiday">Holiday</option>
        <option value="Wishlist">Wishlist</option>
      </select>
    </div>
    <div class="text-center border">
      <div class="border flex justify-between">
        <div class="border w-28">Date</div>
        <div class="">Description</div>
        <div class="border w-28">Actions</div>
      </div>
      <div v-for="todo in categories[category]" :key="todo.id">
        <Todo
          :todo="todo"
          :category="category"
          @DeleteTodo="DeleteTodo"
          @CheckTodo="CheckTodo"
        />
      </div>
    </div>
    <Summary :todos="categories[category]" />
  </div>
</template>

<script>
export default {
  data() {
    return {
      todos: [],
      category: "Work",
      categories: {
        Work: [],
        Holiday: [],
        Wishlist: [],
      },
    };
  },
  methods: {
    AddTodo(todo, category) {
      this.categories[category].push(todo);
    },
    DeleteTodo(todoToDelete, category) {
      console.log(todoToDelete, category);
      let tods = this.categories[category].filter(
        (todo) => todo.id != todoToDelete.id
      );

      this.categories[category] = tods;
    },
    CheckTodo(todoToCheck, category) {
      this.categories[category].forEach((todo) => {
        if (todo.id == todoToCheck.id) {
          todo.check = todoToCheck.check;
        }
      });
    },
  },
};
</script>

<style>
</style>