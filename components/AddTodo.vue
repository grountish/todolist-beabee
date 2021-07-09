<template>
  <div class="w-11/12 flex align-center">
    <input class="border w-full h-6" v-model="todo" type="text" name="" id="" />
    <select name="categories" id="categories" v-model="category">
      <option value="Work">Work</option>
      <option value="Holiday">Holiday</option>
      <option value="Wishlist">Wishlist</option>
    </select>
    <button class="px-6 my-4 border" @click="AddTodo">Save</button>
  </div>
</template>

<script>
export default {
  data() {
    return {
      todo: "",
      category:'Work'
    };
  },
  methods: {
    AddTodo() {
      let todo = {
        date: Date.now(),
        todo: this.todo,
        check: false,
        id: Math.random(),
      };

      this.$emit("AddTodo", todo,this.category);
      this.todo = "";
    },
  },
};
</script>

<style>
</style>