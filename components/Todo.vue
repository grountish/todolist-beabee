<template>
  <div class="border flex justify-between">
    <div class="border px-4 w-28">
      {{ new Date(todo.date).toLocaleString('en-EN',{
   
     hour: "2-digit", minute: "2-digit",day: "numeric",month:"numeric"
}) }}
    </div>
    <input type="text" v-model="todo.todo" v-if="editMode" class="" />
    <div v-else :class="[todo.check ? 'flex items-center justify-between line-through ' : 'flex items-center justify-between']">
      <p> {{ todo.todo }}</p>
    </div>

    <div class="border px-4 w-28  flex items-center justify-between">
      <input
        type="checkbox"
        id=""
        @change="checkTodo(todo)"
        v-model="todo.check"
      />
      <div class="p-1 cursor-pointer" @click="editMode = !editMode">📝</div>
      <div class="p-1 cursor-pointer" @click="DeleteTodo(todo,category)">🗑</div>
    </div>
  </div>
</template>

<script>
export default {
  props: ['todo','category'],

  data() {
    return {
      todos: [],
      editMode: false,
    }
  },
  methods: {
    DeleteTodo(todoToDelete) {
      !todoToDelete.check && this.$emit('DeleteTodo', todoToDelete,this.category)
    },
    checkTodo(todoToCheck) {
      this.$emit('CheckTodo', todoToCheck,this.category)
    },
  },
}
</script>

<style>
</style>