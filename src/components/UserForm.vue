<template>
  <div
    class="q-pa-md full-width bg-white shadow-1 rounded-borders"
    style="max-width: 500px"
  >
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
        <q-btn label="Отправить" type="submit" color="primary"></q-btn>
        <q-btn
          label="Сбросить"
          type="reset"
          color="primary"
          flat
          class="q-ml-sm"
        ></q-btn>
      </div>
    </q-form>
  </div>
</template>

<script setup>
import { defineComponent, ref } from "vue";
import { useQuasar } from "Quasar";

defineComponent({
  name: "UserForm",
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

const $q = useQuasar();
const emit = defineEmits(["submitted"]);

function onSubmit() {
  $q.notify({
    color: "green-4",
    textColor: "white",
    icon: "cloud_done",
    message: "Форма отправлена",
  });

  emit("submitted");
}

function onReset() {
  name.value = "";
  surname.value = "";
  phone.value = "";
  email.value = "";
  message.value = "";
}
</script>
