<template>
  <button @click="onClick">{{ text }}</button>
</template>

<script lang="ts">
import { defineComponent } from 'vue'

export default defineComponent({
  name: 'Button',
  props: {
    text: String,
    onClick: Function
  }
})
</script>

<style scoped>

</style>
