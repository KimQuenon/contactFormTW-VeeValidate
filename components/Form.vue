<script setup>
    import { Form, Field, ErrorMessage  } from 'vee-validate';
    import * as yup from 'yup';
    import { ref } from 'vue';

    //init successMessage
    const successMessage = ref('');

    //array validation rules + empty fields
    const schema = yup.object({
      name: yup.string().required().min(2),
      surname: yup.string().required().min(2),
      email: yup.string().required().email(),
      phone: yup.string().required().min(10),
      message: yup.string().required().min(25),
    });

    //submit form
    const onSubmit = (values, { resetForm }) => {
      resetForm()
      successMessage.value = 'Merci pour votre message!';
      return false;
    }

</script>


<template>
    <div class="container mx-auto">
      <Form method="post" @submit="onSubmit" :validation-schema="schema">
        <div v-if="successMessage" class="bg-green-200 text-green-800 border border-green-600 rounded-md px-4 py-2 mb-4">
          {{ successMessage }}
        </div>

        <div class="mb-4">
          <label>Nom<span class="text-red-600">*</span></label>
          <div class="relative">
            <Field
              type="text"
              name="name"
              class="form-input block w-full border border-gray-300 rounded px-3 py-2"
              placeholder="Votre nom..."
            >
            </Field>
            <ErrorMessage name="name" class="text-xs text-red-500"/>
          </div>
        </div>

        <div class="mb-4">
          <label>Prénom<span class="text-red-600">*</span></label>
          <div class="relative">
            <Field
              type="text"
              name="surname"
              class="form-input block w-full border border-gray-300 rounded px-3 py-2"
              placeholder="Votre prénom..."
            >
            </Field>
            <ErrorMessage name="surname" class="text-xs text-red-500"/>
          </div>
        </div>

        <div class="mb-4">
          <label>Adresse mail<span class="text-red-600">*</span></label>
          <div class="relative">
            <Field
              type="email"
              name="email"
              class="form-input block w-full border border-gray-300 rounded px-3 py-2"
              placeholder="Votre adresse mail..."
            >
            </Field>
            <ErrorMessage name="email" class="text-xs text-red-500"/>
          </div>
        </div>

        <div class="mb-4">
          <label>Téléphone<span class="text-red-600">*</span></label>
          <div class="relative">
            <Field
              type="tel"
              name="phone"
              class="form-input block w-full border border-gray-300 rounded px-3 py-2"
              placeholder="Votre numéro de téléphone..."
            >
            </Field>
            <ErrorMessage name="phone" class="text-xs text-red-500"/>
          </div>
        </div>

        <div class="mb-4">
          <label>Message<span class="text-red-600">*</span></label>
          <div class="relative">
            <Field
              type="text"
              name="message"
              class="form-input block w-full border border-gray-300 rounded px-3 py-2"
              placeholder="Commencez à rédiger..."
              as="textarea"
            >
            </Field>
            <ErrorMessage name="message" class="text-xs text-red-500"/>
          </div>
        </div>
  
        <button type="submit" class="bg-blue-500 text-white px-4 py-2 rounded hover:bg-blue-600 focus:outline-none focus:bg-blue-600">Envoyer</button>
      </Form>
    </div>
  </template>