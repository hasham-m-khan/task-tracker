<template>
  <div class="flex justify-between items-center bg-sky-200 rounded py-2 px-3 my-4">
    <h1> {{ title }} </h1>
    <Button text="Add Task" color="green" intensity="500" @click="$emit('toggle-add-task')"/>
  </div>
</template>

<script>

import Button from './Button'

export default {
  name: 'Header',
  components: {
    Button
  },
  props: {
    title: { type: String, default: 'Title' }
  },
  emits: ['toggle-add-task']
}
</script>

<style scoped>
  h1 {
    font-weight: 600;
    font-size: 1.2rem;
  }
</style>
