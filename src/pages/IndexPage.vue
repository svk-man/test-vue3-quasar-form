<template>
  <q-page class="flex flex-center">
    <q-btn
      label="Открыть модальное окно"
      color="primary"
      @click="form = true"
    ></q-btn>
    <q-dialog v-model="form">
      <user-form />
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
</script>
