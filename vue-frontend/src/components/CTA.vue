<script>
export default {
  name: "CTA",
};
</script>

<template>
  <!-- Call-to-Action Section: Encourages user engagement -->
  <section class="cta">
    <h2>Ready to Create Your Own Portrait?</h2>

    <p>Start transforming your photos today! It's fast, easy and fun.</p>

    <!-- CTA Buttons for navigation -->
    <div class="cta-buttons">
      <!-- Navigate to creation/upload page -->
      <router-link to="/create">
        <button class="primary-btn">Upload Your Photo</button>
      </router-link>

      <!-- Navigate to about page -->
      <router-link to="/about">
        <button class="secondary-btn">Learn More</button>
      </router-link>
    </div>
  </section>
</template>

<style scoped>
/* CTA container */
.cta {
  text-align: center;
  padding: 40px;
  background-color: #2b5d6e;
  color: white;
}

/* CTA title */
.cta h2 {
  margin-top: 10px;
  font-size: 1.8rem;
}

/* Button container */
.cta-buttons {
  margin-top: 20px;
  margin-bottom: 15px;
}

/* Primary action button */
.primary-btn {
  color: #202020;
  padding: 10px 40px;
  border: none;
  cursor: pointer;
  border-radius: 8px;
  font-size: 0.9rem;
  margin-right: 10px;
}

/* Secondary action button */
.secondary-btn {
  color: #202020;
  border: none;
  padding: 10px 25px;
  cursor: pointer;
  border-radius: 8px;
  font-size: 0.9rem;
}
</style>
