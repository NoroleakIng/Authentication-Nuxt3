<template>
  <div
    class="d-flex flex-column justify-space-around align-center text-center h-screen"
  >
    <div>
      <h1 class="mb-15">Welcome</h1>
      <h3>{{ formattedDate }}</h3>
      <h3>{{ formattedTime }}</h3>
    </div>
    <Quotes />
    <div class="d-flex mt-10 ga-10">
      <v-btn
        flat
        color="red"
        rounded="lg"
        class="login-btn text-subtitle-2 text-uppercase"
        @click="goToLogin"
      >
        Login
      </v-btn>
      <v-btn
        variant="tonal"
        rounded="lg"
        class="text-subtitle-2 text-uppercase"
        @click="goToRegister"
      >
        Register
      </v-btn>
      <!-- <v-btn
        flat
        color="red"
        rounded="lg"
        class="login-btn text-subtitle-2 text-uppercase"
        @click="goToHome"
      >
        Logout
      </v-btn> -->
    </div>
  </div>
</template>

<script setup>
import { ref, onMounted, onUnmounted, computed } from "vue";
import { useRouter } from "vue-router";
import dayjs from "dayjs";
import Quotes from "~/components/Quotes.vue";

const router = useRouter();
const currentTime = ref(dayjs());

const updateTime = () => {
  currentTime.value = dayjs();
};

let intervalId;

onMounted(() => {
  intervalId = setInterval(updateTime, 1000);
});
onUnmounted(() => {
  clearInterval(intervalId);
});

const formattedDate = computed(() => currentTime.value.format("DD MMMM YYYY"));
const formattedTime = computed(() => currentTime.value.format("hh:mm:ss A"));

const goToLogin = () => {
  router.push("/login");
};
const goToRegister = () => {
  router.push("/register");
};
const goToHome = () => {
  router.push("/");
};
</script>

<style scoped>
.login-btn {
  box-shadow: 0px 0px 5px rgba(0, 0, 0, 0.2);
}
.login-btn:hover {
  box-shadow: 0px 0px 10px rgba(0, 0, 0, 0.4);
}
</style>
