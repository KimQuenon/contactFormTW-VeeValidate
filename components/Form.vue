<script setup>
    import { Form, Field, ErrorMessage  } from 'vee-validate';

</script>


<template>
    <div>
      <Form @submit="onSubmit" :validation-schema="schema">

        <div class="mb-4">
          <label>Nom<span class="text-red-600">*</span></label>
          <div class="relative">
            <Field
              type="text"
              name="name"
              class="form-input block w-full border border-gray-300 rounded px-3 py-2"
              placeholder="Votre nom..."
              :rules="validateName"
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
              :rules="validateSurname"
            >
            </Field>
            <ErrorMessage name="surname" class="text-xs text-red-500"/>
          </div>
        </div>

        <div class="mb-4">
          <label>Mail<span class="text-red-600">*</span></label>
          <div class="relative">
            <Field
              type="email"
              name="mail"
              class="form-input block w-full border border-gray-300 rounded px-3 py-2"
              placeholder="Votre adresse mail..."
              :rules="validateEmail"
            >
            </Field>
            <ErrorMessage name="mail" class="text-xs text-red-500"/>
          </div>
        </div>

        <div class="mb-4">
          <label>Phone<span class="text-red-600">*</span></label>
          <div class="relative">
            <Field
              type="tel"
              name="phone"
              class="form-input block w-full border border-gray-300 rounded px-3 py-2"
              placeholder="Votre numéro de téléphone..."
              :rules="validatePhone"
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
              :rules="validatePhone"
              as="textarea"
            >
            </Field>
            <ErrorMessage name="message" class="text-xs text-red-500"/>
          </div>
        </div>
  
        <button type="submit" class="btn btn-primary">Envoyer</button>
      </Form>
    </div>
  </template>