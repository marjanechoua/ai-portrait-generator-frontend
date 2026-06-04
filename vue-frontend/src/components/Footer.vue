<script>
export default {
  name: "Footer",
};
</script>

<template>
  <!-- Footer Section: Navigation and contact info -->
  <footer class="footer">
    <!-- Footer Links for main navigation -->
    <div class="footer-links">
      <router-link to="/">Home</router-link>
      <router-link to="/create">Create Portraits</router-link>
      <router-link to="/gallery">Gallery</router-link>
      <router-link to="/about">About Us</router-link>
    </div>

    <!-- Contact Information -->
    <div class="contact-info">
      <p>Contact: support@portrait-generator.com</p>
      <p>&copy; 2025 Portrait Generator. All Rights Reserved.</p>
    </div>
  </footer>
</template>

<style scoped>
/* Footer container */
.footer {
  padding: 20px;
  background-color: #1e3a46;
  color: white;
  text-align: center;
}

/* Footer navigation links */
.footer-links a {
  color: #fff;
  margin: 0 10px;
  text-decoration: none;
  display: inline-block;
  transition: transform 0.3s ease;
}

.footer-links a:hover {
  transform: scale(1.05);
}

/* Social media / additional links */
.social-media a {
  margin: 0 10px;
}
</style>
