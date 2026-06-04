<script>
export default {
  name: "About",
};
</script>

<template>
  <!-- About Section: Explains what the application does -->
  <section class="about">
    <h2>What We Do</h2>

    <p>
      We use cutting-edge AI technology to transform your photos into beautiful,
      artistic portraits.
    </p>

    <!-- Process Steps -->
    <div class="process">
      <!-- Step 1: Upload -->
      <div class="step">
        <i class="fas fa-cloud-upload-alt"></i>
        <p>Upload your photo</p>
      </div>

      <!-- Step 2: Style Selection -->
      <div class="step">
        <i class="fas fa-palette"></i>
        <p>Select a style</p>
      </div>

      <!-- Step 3: Download Result -->
      <div class="step">
        <i class="fas fa-download"></i>
        <p>Download your portrait</p>
      </div>
    </div>
  </section>
</template>

<style scoped>
/* About section container */
.about {
  background-color: #fff;
  padding: 40px;
  text-align: center;
}

/* Section title */
.about h2 {
  font-size: 1.8rem;
}

/* Process layout */
.process {
  display: flex;
  justify-content: space-around;
  margin-top: 40px;
}

/* Individual step container */
.step {
  display: flex;
  flex-direction: column;
  align-items: center;
}

/* Icons styling */
.step i {
  font-size: 50px;
  color: #2b5d6e;
  margin-bottom: 10px;
}
</style>
