<script setup>
import Formik from '@/components/Formik.vue'

const values = reactive({})
const errors = reactive({})
const handleSubmit = reactive({})
const isSubmitting = reactive({})


</script>

<template>
  <Formik :initialValues="['email', 'password']" :validate="'zdzd'" :onSubmit="'r" @values="values" @errors="errors"/>
</template>