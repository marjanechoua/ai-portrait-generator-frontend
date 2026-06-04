<script>
export default {
  name: "Hero"
};
</script>

<template>
  <!-- Hero Section: Main landing banner with headline and CTA -->
  <section class="hero">
    <!-- Hero Text Content -->
    <div class="hero-text">
      <h1>Transform Your Portraits into Stunning AI Art</h1>
      <p>Upload your photo, choose a style, and let our AI work its magic.</p>

      <!-- Call-to-Action Buttons -->
      <div class="cta-buttons">
        <!-- Primary Action: Start creating -->
        <router-link to="/create">
          <button class="primary-btn">Get Started</button>
        </router-link>

        <!-- Secondary Action: Explore gallery -->
        <router-link to="/gallery">
          <button class="secondary-btn">Explore Examples</button>
        </router-link>
      </div>
    </div>
  </section>
</template>

<style scoped>
/* Hero container */
.hero {
  display: flex;
  justify-content: space-between;
  align-items: center;
  height: 500px;
  background-color: #2b5d6e;
}

/* Hero text block */
.hero-text {
  max-width: 50%;
  padding: 50px;
  color: #ffffff;
}

/* Headline */
.hero-text h1 {
  font-size: 2.5rem;
  color: #ffffff;
}

/* CTA buttons container */
.cta-buttons {
  display: flex;
  gap: 10px;
  margin-top: 30px;
}

/* Primary CTA button */
.primary-btn {
  color: #202020;
  padding: 10px 60px;
  border: none;
  border-radius: 8px;
  cursor: pointer;
  font-size: 0.9rem;
}

/* Secondary CTA button */
.secondary-btn {
  padding: 10px 25px;
  border: none;
  border-radius: 8px;
  cursor: pointer;
  font-size: 0.9rem;
  color: #202020;
}
</style>
