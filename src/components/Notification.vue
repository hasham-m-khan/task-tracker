<template>
  <div class="container rounded text-white my-4 px-4" :class="`bg-${ color }-500`">
    <div class="block flex justify-contents-center py-4">
      <span class="material-icons px-2">error_outline</span>
      <span>{{ text }}</span>
    </div>
  </div>
</template>

<script>
export default {
  props: {
    text: String,
    color: String
  }
}
</script>
