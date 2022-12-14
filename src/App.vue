<script setup>
import Formik from '@/components/Formik.vue'
</script>

<template>
  <Formik :initialValues="['email', 'password']" :validate="'zdzd'"/>
</template>