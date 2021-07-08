<template>
  <div>
  
    Summary: {{ returnOutstanding}} Outstanding, {{ returnCompleted}} Completed
  
  </div>
</template>

<script>
export default {
  props:['todos'],
  computed:{
    returnOutstanding() {
      let outstanding = this.todos.filter((todo) => !todo.check)
      return outstanding.length
    },
      returnCompleted() {
      let completed = this.todos.filter((todo) => todo.check)
      return completed.length
    }
  }
}
</script>

<style>
</style>