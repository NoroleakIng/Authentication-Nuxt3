<template>
  <div class="d-flex flex-column justify-center align-center h-screen">
    <v-card
      flat
      rounded="xl"
      class="mx-auto pa-10"
      min-width="500"
      style="box-shadow: 0px 0px 5px rgba(0, 0, 0, 0.2)"
    >
      <v-card-title class="text-center mb-7 pa-0">Register</v-card-title>

      <v-form @submit.prevent="onSubmit">
        <div class="text-subtitle-1 text-medium-emphasis">Full Name</div>
        <v-text-field
          v-model="fullName"
          :readonly="loading"
          :rules="[required]"
          density="compact"
          placeholder="Full name"
          prepend-inner-icon="mdi-account-outline"
          variant="outlined"
        ></v-text-field>

        <div class="text-subtitle-1 text-medium-emphasis">Email</div>
        <v-text-field
          v-model="email"
          :readonly="loading"
          :rules="[required]"
          density="compact"
          placeholder="Email address"
          prepend-inner-icon="mdi-email-outline"
          variant="outlined"
        ></v-text-field>

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

        <div class="d-flex flex-column">
          <v-btn
            block
            color="red"
            type="submit"
            rounded="lg"
            class="login-btn text-subtitle-2 text-uppercase my-5"
            @click="onSubmit"
          >
            Sign up
          </v-btn>
          <v-btn
            block
            variant="tonal"
            rounded="lg"
            class="text-subtitle-2 text-uppercase"
            @click="goToLogin"
          >
            Already have an account
          </v-btn>
        </div>
      </v-form>
    </v-card>
  </div>
</template>

<script setup>
import { ref } from "vue";
import { useRouter } from "vue-router";

const router = useRouter();

const fullName = ref("");
const email = ref("");
const password = ref("");
const visible = ref(false);
const loading = ref(false);

const required = (v) => !!v || "Field is required";

const onSubmit = () => {
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
.login-btn {
  box-shadow: 0px 0px 2px rgba(0, 0, 0, 0.5);
}
.login-btn:hover {
  box-shadow: 0px 0px 5px rgba(0, 0, 0, 0.2);
}
</style>
