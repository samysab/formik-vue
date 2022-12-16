<script setup>
  import {reactive, ref} from "vue";
  import Field from '@/components/Field.vue'


  const props = defineProps({
    initialValues: {
      type: Array,
      required: true
    },
    validate: {
      type: Function,
      required: true
    },
    onSubmit: {
      type: Function,
      required: true
    }
  })

  const values = reactive(props.initialValues)


  const errors = ref({})
  const isSubmitting = ref(false)


  const handleSubmit = (e) => {
    errors.value = props.validate(values)
    if (Object.keys(errors).length === 0) {
      props.onSubmit(values)
    }
  }
</script>

<template>
  <form @submit.prevent=handleSubmit>
    <Field v-for="(value, index) in this.values"
           :key="index"
           :name="value.name"
           :as="value.as"
    />
    <button type="submit" v-bind:disabled="isSubmitting">Submit</button>
  </form>
</template>