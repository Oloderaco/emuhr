<template>
  <button class="button" :style="btnStyle">{{ label }}</button>
</template>

<script setup>
import { computed } from 'vue'

const props = defineProps({
  label: { type: String, default: 'Button' },
  size: { type: String, default: 'md' }, // sm, md, lg
  bgColor: { type: String, default: '#7A43FA' },
  textColor: { type: String, default: '#FFFFFF' }
})

const btnStyle = computed(() => {
  let padding = '12px 24px'
  let fontSize = '16px'

  if (props.size === 'sm') {
    padding = '8px 16px'
    fontSize = '14px'
  } else if (props.size === 'lg') {
    padding = '16px 32px'
    fontSize = '18px'
  }

  return {
    padding,
    fontSize,
    backgroundColor: props.bgColor,
    color: props.textColor,
  }
})
</script>

<style scoped>
.button {

  border: none;
  border-radius: 12px;
  cursor: pointer;
  font-weight: 600;
  transition: background 0.2s ease, transform 0.15s ease;
}
.button:hover {
  transform: translateY(-1px);
  background: #8e5bff;
}
.button:active {
  transform: translateY(0);
}
</style>