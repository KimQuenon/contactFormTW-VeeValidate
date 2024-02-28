
<template>
  <div>
    <Form @submit="onSubmit" :validation-schema="schema">
      <Field name="email" type="email" class="form-control" :rules="validateEmail"/>
      <ErrorMessage name="email" />

      <button type="submit" class="btn btn-primary">Sign up for newsletter</button>
    </Form>
  </div>
</template>

<script setup>
  import { Form, Field, ErrorMessage  } from 'vee-validate';

   const onSubmit = (values) => {
    console.log(values)
   }

   const validateEmail = (value)=> {
      // if the field is empty
      if (!value) {
        return 'This field is required';
      }

      // if the field is not a valid email
      const regex = /^[A-Z0-9._%+-]+@[A-Z0-9.-]+\.[A-Z]{2,4}$/i;
      if (!regex.test(value)) {
        return 'This field must be a valid email';
      }

      // All is good
      return true;
    }

</script>

