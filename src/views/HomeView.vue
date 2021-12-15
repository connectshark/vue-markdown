<script setup>
import { computed, ref } from 'vue'
import { marked } from 'marked'

const input = ref('# Hello')

const compiledMarkdown = computed(() => {
  return marked(input.value, { sanitize: true })
})

const update = (e) => {
  input.value = e.target.value
} 
</script>

<template>
<main id="editor">
  <textarea :value="input" @input="update"></textarea>
  <div v-html="compiledMarkdown"></div>
</main>
</template>


<style scoped>
#editor{
  height: 100%;
}
#editor textarea {
  border: none;
  border-right: 1px solid #ccc;
  resize: none;
  outline: none;
  background-color: #f6f6f6;
  font-size: 14px;
  font-family: "Monaco", courier, monospace;
  padding: 20px;
  height: 100%;
}
#editor div{
  padding: 0 20px;
}
code {
  color: #f66;
}
#editor textarea,
#editor div {
  display: inline-block;
  width: 49%;
  vertical-align: top;
  box-sizing: border-box;
}
</style>