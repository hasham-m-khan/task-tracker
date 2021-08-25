<template>
  <div class="container mx-auto">
    <Header title="Task Tracker" @toggle-add-task="this.hideForm = !this.hideForm"/>
    <Notification :class="[(this.displayNotice) ? '' : 'hidden']" :text="notificationText" :color="noticeColor" />
    <AddTask :class="[(this.hideForm) ? 'hidden' : '']" @show-notification="showNotification($event)" @add-task="onAddTask($event)" />
    <Tasks :tasks="tasks" @delete-task="onDeleteTask" @toggle-reminder="onToggleReminder"/>
  </div>
</template>

<script>
import Header from './components/Header.vue'
import Tasks from './components/Tasks.vue'
import AddTask from './components/AddTask'
import Notification from './components/Notification'

export default {
  name: 'App',
  components: {
    Header,
    Tasks,
    AddTask,
    Notification
  },
  data () {
    return {
      tasks: [],
      hideForm: false,
      displayNotice: false,
      notificationText: '',
      noticeColor: ''
    }
  },
  methods: {
    onAddTask (newTask) {
      this.tasks = [...this.tasks, newTask]

      this.displayNotice = true
      this.notificationText = 'Task successfully added!'
      this.noticeColor = 'green'
    },
    onDeleteTask (id) {
      this.tasks = this.tasks.filter((task) => task.id !== id)
    },
    onToggleReminder (id) {
      this.tasks = this.tasks.map((task) =>
        (task.id === id) ? { ...task, reminder: !task.reminder } : task
      )
    },
    showNotification (event) {
      this.displayNotice = true
      this.notificationText = event[0]
      this.noticeColor = event[1]
    }
  },
  created () {
    this.tasks = [
      { id: 1, title: 'Doctor\'s appointment', text: 'Doctor\'s appointment for general checkup and yearly flu shot', date: '2021/8/22', reminder: true },
      { id: 2, title: 'Check mail', text: 'Expecting mail from an important client', date: '2021/8/15', reminder: true },
      { id: 3, title: 'Car servicing', text: '6 month oil change and car servicing is due. DO NOT FORGET', date: '2021/10/12', reminder: true },
      { id: 4, title: 'Holiday shopping', text: 'Holiday season at the end of the year. Be sure to grab necessary items as they will be on discount', date: '2021/12/21', reminder: false }
    ]
  }
}
</script>

<style>
  @import url('https://fonts.googleapis.com/css2?family=Poppins&display=swap');

  html, body, * {
    font-family: 'Poppins', sans-serif;
  }

</style>
