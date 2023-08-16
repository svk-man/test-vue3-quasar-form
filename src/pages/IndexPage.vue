<template>
  <q-page class="flex flex-center">
    <q-btn
      label="Открыть модальное окно"
      color="primary"
      @click="openDialog"
    ></q-btn>
    <q-dialog v-model="form">
      <user-form v-on:submitted="closeDialog" />
    </q-dialog>
  </q-page>
</template>

<script setup>
import { defineComponent, ref } from "vue";
import UserForm from "../components/UserForm.vue";

defineComponent({
  name: "IndexPage",
});

const form = ref(false);

function openDialog() {
  form.value = true;
}

function closeDialog() {
  form.value = false;
}
</script>
