<script>
export default {
  name: "ResultSection",
  props: {
    image: String, // The generated image URL
    loading: Boolean // Loading state
  }
};
</script>

<template>
  <!-- Display loading, result, or fallback message -->
  <div>
    <!-- Show spinner while generating -->
    <div v-if="loading" class="loading-spinner">Loading...</div>

    <!-- Show generated image when available -->
    <div v-else-if="image" class="result">
      <img :src="image" alt="Generated Image" />
      <a :href="image" download="generated-image.png">Download</a>
    </div>

    <!-- Fallback message -->
    <div v-else class="no-result">No result available</div>
  </div>
</template>

<style scoped>
.loading-spinner {
  text-align: center;
  font-size: 18px;
  font-weight: bold;
  color: #2b5d6e;
  margin-top: 20px;
}

.result {
  text-align: center;
  margin-top: 20px;
}

.result img {
  max-width: 100%;
  border-radius: 8px;
  margin-bottom: 10px;
}

.result a {
  display: inline-block;
  text-decoration: none;
  color: #fff;
  background-color: #2b5d6e;
  padding: 8px 15px;
  border-radius: 5px;
  font-weight: bold;
}

.result a:hover {
  background-color: #3f8ca0;
}

.no-result {
  text-align: center;
  font-size: 16px;
  color: #555;
  margin-top: 20px;
}
</style>
