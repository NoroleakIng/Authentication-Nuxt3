<template>
  <div class="d-flex flex-column align-center w-100">
    <div class="quote-container text-body-1">
      {{ currentQuote }} - {{ currentAuthor }}
    </div>
    <v-btn prepend-icon="mdi-reload" @click="reloadPage">More Quotes</v-btn>
  </div>
</template>

<script setup>
import { ref } from "vue";
import { getQuote } from "inspirational-quotes";

const currentQuote = ref("");
const currentAuthor = ref( "" );

const updateQuote = () => {
  const quote = getQuote();
  currentQuote.value = quote.text;
  currentAuthor.value = quote.author;
};
updateQuote();

const reloadPage = () => {
  window.location.reload();
};
</script>

<style scoped>
.quote-container {
  text-align: center;
  padding: 20px;
  width: 80%;
  background-color: #f9f9f9;
  border: 1px solid #ddd;
  border-radius: 10px;
  margin-bottom: 50px;
}
</style>
