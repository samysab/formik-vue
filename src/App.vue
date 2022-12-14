<script setup>
import {reactive} from "vue";

import Formik from '@/components/Formik.vue'

const values = reactive({})
const errors = reactive({})

const initialValues = reactive([
  {
    name: 'name',
    as: 'input'
  },
  {
    name: 'email',
    as: 'input'
  },
  {
    name: 'password',
    as: 'input'
  },
  {
    name: 'test',
    as: 'select'
  }
]);

function validate(values) {
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

function onSubmit(values) {
  console.log('submitting', values)
}


</script>

<template>
  <Formik :initialValues="initialValues" :validate="validate" :onSubmit="onSubmit" @values="values" @errors="errors"/>
</template>