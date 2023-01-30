<template>
  <div>
    <v-btn
      color="primary"
      class="text-none"
      rounded
      depressed
      :loading="isSelecting"
      @click="onButtonClick"
    >
      Select Image
    </v-btn>
    <input
      ref="uploader"
      class="d-none"
      type="file"
      accept="image/*"
      @change="onFileChanged"
    />
  </div>
</template>

<script>
export default {
  name: "FileInput",

  data() {
    return { selectedFile: null, isSelecting: false };
  },

  mounted() {},

  methods: {
    onButtonClick() {
      this.isSelecting = true;
      window.addEventListener(
        "focus",
        () => {
          this.isSelecting = false;
        },
        { once: true }
      );

      this.$refs.uploader.click();
    },
    onFileChanged(e) {
      this.selectedFile = e.target.files[0];

      // do something
    },
  },
};
</script>

<style lang="scss" scoped></style>
