<script>
import { ref } from "vue";

import ImageUpload from "../components/ImageUpload.vue";
import StyleSelection from "../components/StyleSelection.vue";
import ResultSection from "../components/ResultSection.vue";

export default {
  name: "GenerateView",
  components: {
    ImageUpload,
    StyleSelection,
    ResultSection,
  },
  setup() {
    // Uploaded image file
    const image = ref(null);

    // Selected artistic style
    const selectedStyle = ref(null);

    // Generated image returned by backend
    const generatedImage = ref(null);

    // Loading state during API request
    const isProcessing = ref(false);

    /**
     * Handles image upload from child component
     */
    const handleImageUpload = (uploadedImage) => {
      image.value = uploadedImage;
    };

    /**
     * Handles style selection from child component
     */
    const handleStyleSelection = (style) => {
      selectedStyle.value = style;
    };

    /**
     * Sends image + style to backend API and retrieves generated portrait
     */
    const applyStyle = async () => {
      if (!image.value || !selectedStyle.value) return;

      isProcessing.value = true;

      const formData = new FormData();
      formData.append("image", image.value);
      formData.append("style", selectedStyle.value);

      try {
        const response = await fetch("YOUR_BACKEND_URL/api/generate-portrait", {
          method: "POST",
          body: formData,
        });

        if (!response.ok) {
          throw new Error("Network response was not ok");
        }

        const data = await response.json();

        // Store generated image if available
        if (data.generated_image) {
          generatedImage.value = data.generated_image;
        } else {
          console.error("Invalid response format:", data);
        }
      } catch (error) {
        console.error("Error while generating portrait:", error);
      } finally {
        isProcessing.value = false;
      }
    };

    return {
      image,
      selectedStyle,
      generatedImage,
      isProcessing,
      handleImageUpload,
      handleStyleSelection,
      applyStyle,
    };
  },
};
</script>

<template>
  <!-- Main container for AI portrait generation view -->
  <div class="generate-view-container">
    <div class="main-content">
      <h1>Free AI Portrait Generator</h1>

      <p>
        Create stunning, AI-generated portraits tailored to your unique style
        using our free tool.
      </p>

      <!-- Image upload component -->
      <ImageUpload @file-chosen="handleImageUpload" />

      <!-- Style selection component -->
      <StyleSelection @style-selected="handleStyleSelection" />

      <!-- Trigger generation only when both inputs are available -->
      <button
        v-if="image && selectedStyle"
        @click="applyStyle"
        class="apply-style-button"
      >
        Apply Style
      </button>

      <!-- Result / loading display -->
      <ResultSection :image="generatedImage" :loading="isProcessing" />
    </div>
  </div>
</template>

<style scoped>
/* Page wrapper */
.generate-view-container {
  display: flex;
  flex-direction: column;
  align-items: center;
  margin: 20px;
}

/* Main content container */
.main-content {
  max-width: 900px;
  width: 100%;
}

/* Page title */
h1 {
  font-size: 2rem;
  margin-bottom: 10px;
}

/* Generate button */
.apply-style-button {
  background-color: #4caf50;
  color: white;
  border: none;
  padding: 10px 20px;
  font-size: 16px;
  cursor: pointer;
}

.apply-style-button:hover {
  background-color: #45a049;
}
</style>
