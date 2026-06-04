<script>
export default {
  name: "StyleSelection",
  props: {
    styles: {
      type: Array,
      required: true
    },
    selectedStyle: {
      type: String,
      required: true
    }
  },
  methods: {
    /**
     * Emit selected style to parent component
     * @param {String} style - Name of the selected style
     */
    selectStyle(style) {
      this.$emit("style-selected", style);
    }
  }
};
</script>

<template>
  <!-- Display available style options -->
  <div class="style-options">
    <div
      v-for="(style, index) in styles"
      :key="index"
      class="style-option"
      :data-style="style.name"
      @click="selectStyle(style.name)"
      :class="{ selected: selectedStyle === style.name }"
    >
      <img :src="style.image" :alt="style.name" />
      <p>{{ style.name }}</p>
    </div>
  </div>
</template>

<style scoped>
.style-options {
  display: flex;
  flex-wrap: wrap;
  gap: 15px;
  justify-content: center;
  margin-top: 20px;
}

.style-option {
  cursor: pointer;
  text-align: center;
  transition: transform 0.2s ease;
}

.style-option img {
  width: 120px;
  height: 120px;
  object-fit: cover;
  border-radius: 8px;
  transition:
    border 0.2s ease,
    transform 0.2s ease;
}

.style-option p {
  margin-top: 5px;
  font-weight: 500;
}

.style-option:hover {
  transform: scale(1.05);
}

.style-option.selected img {
  border: 3px solid #3f8ca0;
}
</style>
