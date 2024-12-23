<template>
  <div class="d-flex flex-column justify-center align-center h-screen">
    <v-card
      flat
      class="mx-auto pa-10"
      rounded="xl"
      min-width="500"
      style="box-shadow: 0px 0px 5px rgba(0, 0, 0, 0.2)"
    >
      <v-btn
        variant="plain"
        prepend-icon="mdi-chevron-left"
        class="pa-0"
        @click="goToLogin"
      >
        Back to Login
      </v-btn>

      <v-card-title class="text-center my-5 pa-0">
        Reset Password
      </v-card-title>

      <v-form v-model="form" @submit.prevent="onSubmit">
        <div
          class="text-subtitle-1 text-medium-emphasis d-flex align-center justify-space-between"
        >
          Password
        </div>
        <v-text-field
          v-model="password"
          :readonly="loading"
          :rules="[required]"
          :append-inner-icon="visible ? 'mdi-eye-off' : 'mdi-eye'"
          :type="visible ? 'text' : 'password'"
          density="compact"
          placeholder="Enter your password"
          prepend-inner-icon="mdi-lock-outline"
          variant="outlined"
          @click:append-inner="visible = !visible"
        ></v-text-field>

        <div
          class="text-subtitle-1 text-medium-emphasis d-flex align-center justify-space-between"
        >
          Confirm Password
        </div>
        <v-text-field
          v-model="confirmPassword"
          :readonly="loading"
          :rules="[required]"
          :append-inner-icon="visible ? 'mdi-eye-off' : 'mdi-eye'"
          :type="visible ? 'text' : 'password'"
          density="compact"
          placeholder="Enter your confirm password"
          prepend-inner-icon="mdi-lock-outline"
          variant="outlined"
          @click:append-inner="visible = !visible"
        ></v-text-field>

        <v-btn
          block
          color="red"
          type="submit"
          rounded="lg"
          class="reset-password-btn text-subtitle-2 text-uppercase mt-5"
          :loading="loading"
          @click="validate, goToLogin()"
        >
          Reset Password
        </v-btn>
      </v-form>
    </v-card>
  </div>
</template>

<script setup>
import { ref } from "vue";
import { useRouter } from "vue-router";

const router = useRouter();
const form = ref(false);
const password = ref("");
const confirmPassword = ref(false);
const visible = ref(false);
const loading = ref(false);

const required = (v) => !!v || "Field is required";

const onSubmit = () => {
  if (!form.value) return;
  loading.value = true;
  setTimeout(() => {
    loading.value = false;
  }, 2000);
};

const goToLogin = () => {
  router.push("/login");
};
</script>

<style scoped>
.back-btn {
  padding: 0;
}
.back-btn:hover {
  color: red;
  background-color: transparent;
}
.reset-password-btn {
  box-shadow: 0px 0px 2px rgba(0, 0, 0, 0.5);
}
.reset-password-btn:hover {
  box-shadow: 0px 0px 5px rgba(0, 0, 0, 0.2);
}
</style>
