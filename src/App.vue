<template>
  <div>
    <Nav class="mb-6" />
    <div class="flex justify-center">
      <Rings />
    </div>
    <Footer />
  </div>
</template>

<script>
import Rings from "./components/Rings.vue";
import Nav from "./components/Nav.vue";
import Footer from "./components/Footer.vue"

export default {
  name: "App",
  components: {
    Rings,
    Nav,
    Footer
  }
};
</script>

<style>

</style>
