<template>
  <div class="">
    <input class="w-11/12 border" v-model="todo" type="text" name="" id="" />
    <button class="px-6 my-4 border" @click="AddTodo">Save</button>
  </div>
</template>

<script>
export default {
  data() {
    return {
      todo: '',
    }
  },
  methods: {
    AddTodo() {
      let todo = {
          date: Date.now(),
          todo:this.todo,
          check:false,
          id:Math.random()
      }
    
      this.$emit('AddTodo', todo )
      this.todo = ''
    },
  },
}
</script>

<style>
</style>