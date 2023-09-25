<script setup lang="ts">
defineProps({
  label: {
    type: String,
    default: ''
  },
  value: {
    type: String,
    default: '?'
  }
})
</script>

<template>
  <div>
    <input class="input__text" type="text" required="required"  :value="value" autofocus/>
    <div v-if="label" class="input__message">{{ label }}</div>
  </div>
</template>

<style scoped>
.input__text {
  background: none;
  font-size: 1.5rem;
  font-weight: bold;
  margin-top: 2rem;
  padding: 10px 10px 10px 5px;
  display: block;
  width: 100%;
  border: none;
  border-radius: 0;
  border-bottom: 2px solid var(--color-text);
  word-spacing: 12px;
  text-align: center;
  outline: none;
  color: var(--color-input-text);
}

.input__message {
  margin-top: 10px;
  font-size: .75rem;
  width: 100%;
  text-align: center;
}
</style>
