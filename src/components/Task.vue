<template>
  <div class='container rounded bg-gray-100 my-4 pb-0.5 shadow-md' :class="[(this.task.reminder) ? 'border-b-4 border-orange-500 rounded': '']">
    <div class="flex justify-between items-center px-3 py-2">
      <span class="text-lg font-bold text-gray-900">{{ task.date }}</span>
      <div>
        <span @click="$emit('toggle-reminder', id)" class="bg-yellow-400 rounded px-2 text-white"><i class="fas fa-exclamation"></i></span>
        <span class="bg-orange-400 rounded px-1 mx-1 text-white"><i class="far fa-window-minimize"></i></span>
        <span @click="$emit('delete-task', id)" class="bg-red-500 rounded px-1.5 text-white"><i class="fas fa-times"></i></span>
      </div>
    </div>
    <span class="block px-3 rounded font-bold text-green-700">
      {{ task.title }}
    </span>
    <div class="mb-4 px-3 rounded">
      {{ task.text }}
    </div>
  </div>
</template>

<script>

export default {
  name: 'Task',
  props: {
    task: Object
  },
  emits: ['delete-task', 'toggle-reminder']
}
</script>

<style scoped>

</style>
