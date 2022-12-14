<script setup>
  const props = defineProps({
    name: {
      type: String,
      required: true
    },
    as: {
      type: String,
      required: false
    }
  })
</script>

<template>
  <component :is="props.as" :name="props.name">
    <slot></slot>
  </component>
</template>