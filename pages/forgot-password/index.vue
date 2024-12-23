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
        Forgot Password
      </v-card-title>

      <v-form v-model="form" @submit.prevent="onSubmit">
        <div class="text-subtitle-1 text-medium-emphasis">Email</div>
        <v-text-field
          v-model="email"
          :readonly="loading"
          :rules="[required]"
          density="compact"
          placeholder="Enter your email address"
          prepend-inner-icon="mdi-email-outline"
          variant="outlined"
        ></v-text-field>

        <v-btn
          block
          color="red"
          type="submit"
          rounded="lg"
          class="forgot-password-btn text-subtitle-2 text-uppercase mt-5"
          :loading="loading"
          @click="validate, goToResetPassword()"
        >
          Forgot Password
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
const email = ref("");
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
const goToResetPassword = () => {
  router.push("/reset-password");
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
.forgot-password-btn {
  box-shadow: 0px 0px 2px rgba(0, 0, 0, 0.5);
}
.forgot-password-btn:hover {
  box-shadow: 0px 0px 5px rgba(0, 0, 0, 0.2);
}
</style>
