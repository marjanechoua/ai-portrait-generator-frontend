<script>
import Hero from "../components/Hero.vue";
import About from "../components/About.vue";
import Gallery from "../components/Gallery.vue";
import CTA from "../components/CTA.vue";
import Footer from "../components/Footer.vue";

export default {
  name: "App",
  components: {
    Hero,
    About,
    Gallery,
    CTA,
    Footer,
  },
};
</script>

<template>
  <div>
    <!-- Hero Section: Main landing area with key information -->
    <Hero />

    <!-- About Section: Describes the application and its purpose -->
    <About />

    <!-- Gallery Section: Displays example images and styles -->
    <Gallery />

    <!-- CTA Section: Call-to-action, e.g., upload or try the app -->
    <CTA />

    <!-- Footer Section: Application footer with links or credits -->
    <Footer />
  </div>
</template>

<style>
/* Global styles for the application */
body {
  font-family: Arial, sans-serif;
  margin: 0;
  padding: 0;
  background-color: #ffffff;
}

/* Fade transition for smooth UI animations */
.fade-enter-active,
.fade-leave-active {
  transition: opacity 0.5s ease;
}

.fade-enter,
.fade-leave-to {
  opacity: 0;
}
</style>
