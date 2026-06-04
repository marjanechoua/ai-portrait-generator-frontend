<script>
export default {
  name: "ImageUpload",

  data() {
    return {
      // Tracks whether a drag operation is active
      isDragOver: false,

      // Stores the preview image URL
      previewImage: null
    };
  },

  methods: {
    /**
     * Opens the hidden file input when user clicks the upload area
     */
    triggerFileInput() {
      this.$refs.fileInput.click();
    },

    /**
     * Handles file selection via file picker
     */
    handleFileChange(event) {
      const file = event.target.files[0];

      if (file) {
        // Create temporary preview URL for selected image
        this.previewImage = URL.createObjectURL(file);

        // Send selected file to parent component
        this.$emit("file-chosen", file);
      }
    },

    /**
     * Handles dragover event (visual feedback)
     */
    handleDragOver(event) {
      event.preventDefault();
      this.isDragOver = true;
    },

    /**
     * Handles drag leave event (reset UI state)
     */
    handleDragLeave() {
      this.isDragOver = false;
    },

    /**
     * Handles file drop event
     */
    handleDrop(event) {
      event.preventDefault();
      this.isDragOver = false;

      const file = event.dataTransfer.files[0];

      if (file) {
        this.previewImage = URL.createObjectURL(file);
        this.$emit("file-chosen", file);
      }
    }
  },

  mounted() {
    // Register drag & drop event listeners on component mount
    const uploadArea = this.$el;

    uploadArea.addEventListener("dragover", this.handleDragOver);
    uploadArea.addEventListener("dragleave", this.handleDragLeave);
    uploadArea.addEventListener("drop", this.handleDrop);
  },

  beforeDestroy() {
    // Clean up event listeners when component is destroyed
    const uploadArea = this.$el;

    uploadArea.removeEventListener("dragover", this.handleDragOver);
    uploadArea.removeEventListener("dragleave", this.handleDragLeave);
    uploadArea.removeEventListener("drop", this.handleDrop);
  }
};
</script>

<template>
  <!-- Image upload component with drag & drop support -->
  <div
    class="upload-area"
    @click="triggerFileInput"
    :class="{ dragover: isDragOver }"
  >
    <!-- Hidden file input -->
    <input
      type="file"
      ref="fileInput"
      accept="image/*"
      @change="handleFileChange"
      style="display: none"
    />

    <p>Drag & drop your file here or click to upload</p>

    <!-- Image preview -->
    <div v-if="previewImage" id="preview">
      <img :src="previewImage" alt="Preview" />
    </div>
  </div>
</template>

<style scoped>
/* Upload container */
.upload-area {
  border: 2px dashed #ccc;
  padding: 20px;
  text-align: center;
  cursor: pointer;
  border-radius: 8px;
  transition: background-color 0.2s ease-in-out;
}

/* Drag-over visual feedback */
.upload-area.dragover {
  background-color: rgba(0, 255, 0, 0.1);
  border-color: #4caf50;
}

/* Preview image styling */
#preview img {
  max-width: 100%;
  height: auto;
  margin-top: 15px;
}
</style>
