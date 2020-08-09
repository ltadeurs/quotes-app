<template>
  <div id="app">
    <background/>
    <QuoteApi msg="Quotes app" />
    <Footer copyright="Copyright © 2020 Luuk van Deursen" />
  </div>
</template>

<script>
import QuoteApi from "./components/QuoteApi.vue";
import Footer from "./components/Footer.vue";
import Background from "./components/Background.vue";

export default {
  name: "App",
  components: {
    Background,
    QuoteApi,
    Footer
  },
};
</script>

<style src="./assets/styles/style.css">
</style>
