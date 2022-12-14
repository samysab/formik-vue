<script setup>
  import {reactive} from "vue";

  const values = reactive({})
  const errors = reactive({})
  const handleSubmit = reactive({})
  const isSubmitting = reactive({})

  const $emit = defineEmits({
    submit: (data) => {
      return(
          data
      )
    }
  })

  const onSubmit = (e) => {
    $emit('submit', values)
  }

  function validate(values) {
    if (!values.email) {
      this.errors.email = 'Required'
    } else if (
      !/^[A-Z0-9._%+-]+@[A-Z0-9.-]+\.[A-Z]{2,4}$/i.test(values.email)
    ) {
      errors.email = 'Invalid email address'
    }
    return errors
  }
</script>

<template>
  <form @submit.prevent="handleSubmit">
    <button type="submit">Submit</button>
  </form>
</template>