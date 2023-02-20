<script setup>
import TheTranslator from './components/TheTranslator.vue';
</script>

<template>
  <v-app>
    <v-main class="d-flex align-center bg-blue-grey-lighten-1">
      <v-container>
        <TheTranslator title="GPT Translator" />
      </v-container>
    </v-main>
  </v-app>
</template>

<style scoped>
.logo {
  height: 6em;
  padding: 1.5em;
  will-change: filter;
  transition: filter 300ms;
}
.logo:hover {
  filter: drop-shadow(0 0 2em #646cffaa);
}
.logo.vue:hover {
  filter: drop-shadow(0 0 2em #42b883aa);
}
</style>
