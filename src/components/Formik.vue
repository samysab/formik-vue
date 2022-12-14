<script setup>
  import {reactive} from "vue";

  const values = reactive({})
  const errors = reactive({})
  const isSubmitting = reactive({})

  const $emit = defineEmits({
    submit: (data) => {
      return(
          data !== null
      )
    }
  })

  const onSubmit = (e) => {
    $emit('submit', values)
  }

//validate function
  const validate = (values) => {
    const errors = {}
    if (!values.email) {
      errors.email = 'Required'
    } else if (
      !/^[A-Z0-9._%+-]+@[A-Z0-9.-]+\.[A-Z]{2,4}$/i.test(values.email)
    ) {
      errors.email = 'Invalid email address'
    }
    return errors
  }

  const handleSubmit = (e) => {
    e.preventDefault()
    errors = validate(values)
    if (Object.keys(errors).length === 0) {
      onSubmit(values)
    }
  }
</script>

<template>
  <form @submit.prevent="handleSubmit">
    <button type="submit">Submit</button>
  </form>
</template>