<template>
  <q-page class="flex flex-center">
    <div class="q-pa-md full-width" style="max-width: 500px">
      <q-form @submit="onSubmit" @reset="onReset" class="q-gutter-md">
        <q-input
          filled
          v-model="name"
          label="Ваше имя *"
          hint="Имя"
          lazy-rules
          :rules="[
            (val) => !!val || 'Пожалуйста, введите имя',
            (val) =>
              val.length <= 100 || 'Имя должно содержать не более 100 символов',
          ]"
        ></q-input>

        <q-input
          filled
          v-model="surname"
          label="Ваша фамилия"
          hint="Фамилия"
          lazy-rules
          :rules="[
            (val) =>
              val.length <= 100 ||
              'Фамилия должна содержать не более 100 символов',
          ]"
        ></q-input>

        <q-input
          filled
          v-model="phone"
          label="Телефон *"
          mask="+7(###) ### - ## - ##"
          hint="Формат: +7(###) ### - ## - ##"
          lazy-rules
          :rules="[
            (val) =>
              (val && val.length === '+7(###) ### - ## - ##'.length) ||
              'Пожалуйста, введите телефон',
          ]"
        ></q-input>

        <q-input
          filled
          v-model="email"
          label="Email *"
          type="email"
          hint="Email"
          lazy-rules
          :rules="[(val) => !!val || 'Пожалуйста, введите email', isValidEmail]"
        ></q-input>

        <q-input
          v-model="message"
          filled
          type="textarea"
          lazy-rules
          :rules="[
            (val) =>
              val.length <= 500 ||
              'Сообщение должно содержать не более 500 символов',
          ]"
        ></q-input>

        <div>
          <q-btn label="Submit" type="submit" color="primary"></q-btn>
          <q-btn
            label="Reset"
            type="reset"
            color="primary"
            flat
            class="q-ml-sm"
          ></q-btn>
        </div>
      </q-form>
    </div>
  </q-page>
</template>

<script setup>
import { defineComponent, ref } from "vue";

defineComponent({
  name: "IndexPage",
});

const name = ref("");
const surname = ref("");
const phone = ref("");
const email = ref("");
const message = ref("");

function isValidEmail(val) {
  const emailPattern =
    /^(?=[a-zA-Z0-9@._%+-]{6,254}$)[a-zA-Z0-9._%+-]{1,64}@(?:[a-zA-Z0-9-]{1,63}\.){1,8}[a-zA-Z]{2,63}$/;
  return emailPattern.test(val) || "Некорректный email";
}
</script>
