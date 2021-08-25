<template>
    <button
      class="px-6 py-2 rounded transition duration-500"
      :class="setColor()"
    >
      {{ text }}
    </button>
</template>

<script>
export default {
  name: 'Button',
  props: ['text', 'color', 'intensity'],
  methods: {
    setColor () {
      if (+this.intensity <= 400) {
        return `bg-${this.color}-${+this.intensity} hover:bg-${this.color}-${+this.intensity + 100} text-black`
      }
      return `bg-${this.color}-${+this.intensity} hover:bg-${this.color}-${+this.intensity - 200} text-white`
    }
  }
}
</script>

<style scoped>
  button {
    font-weight: bold;
  }
</style>
