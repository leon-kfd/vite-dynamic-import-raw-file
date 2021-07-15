<template>
  Hello.
  <br>
  <button @click="load(1)">Load File1</button>
  <button @click="load(2)">Load File2</button>
  <pre>{{current}}</pre>
</template>

<script>
import { ref } from 'vue'
export default {
  setup() {
    const current = ref('')
    return {
      current,
      async load(index) {
        const file = await import(`./source/file${index}.md?raw`)
        current.value = file.default
        console.log('file', file)
      }
    }
  }
}
</script>

<style>
</style>
