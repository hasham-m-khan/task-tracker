<template>
  <form class="bg-gray-100 py-3 px-3 rounded" @submit="onSubmit">
    <label for="title">Title</label>
    <input type="text" class="block w-full h-8 pl-3 mb-2" id="title" placeholder="Add title here" v-model="title"/>
    <label for="desc">Description</label>
    <textarea type="textbox" class="block w-full h-24 pl-3 mb-2" id="desc" placeholder="Add task description here ..." rows="10" v-model="text"> </textarea>
    <div class="flex gap-x-3">
      <div class="flex-grow">
        <label for="date">Date</label>
        <input type="date" class="block w-full h-8 pl-3 mb-2" id="date" placeholder="Add title here" v-model="date"/>
      </div>
      <div class="flex-grow">
        <label for="time">Time</label>
        <input type="time" class="block w-full h-8 pl-3 mb-2" id="time" placeholder="Add title here"  v-model="time"/>
      </div>
    </div>
    <div class="block mb-6">
      <label for="reminder">Set reminder?</label>
      <input type="checkbox" class="mx-2" id="reminder" name="reminder" v-model="reminder">
    </div>
    <div class="flex justify-end">
      <Button text="Save" color="blue" intensity="300"/>
    </div>
  </form>
</template>

<script>
import Button from './Button'

export default {
  name: 'AddTask',
  components: {
    Button
  },
  data () {
    return {
      title: '',
      text: '',
      date: '',
      time: '',
      reminder: false
    }
  },
  methods: {
    onSubmit (e) {
      e.preventDefault()

      if (!this.title) {
        const msg = 'Invalid submission. Please verify the form has been properly filed and submit again.'
        const color = 'red'
        this.$emit('show-notification', [msg, color])
        return
      }

      const newTask = {
        id: Math.floor(Math.random() * 100000),
        title: this.title,
        text: this.text,
        date: this.date + ' ' + this.time,
        reminder: this.reminder
      }

      this.$emit('add-task', newTask)
    }
  }
}
</script>

<style>
  textarea {
    resize: none;
  }
</style>
