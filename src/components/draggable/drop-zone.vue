<template>
  <v-card
    class="drop-zone"
    :class="{ active: isActive }"
    @dragenter.prevent="toggleActive"
    @dragleave.prevent="toggleActive"
    @dragover.prevent
    @drop.prevent="
      toggleActive();
      passToParent($event);
    "
  >
    <v-card-text>
      <v-row justify="center">
        <v-col cols="6">
          <v-img src="../../assets/image.svg"></v-img>
        </v-col>
        <v-col cols="12" class="text-center">Drag & Drop your image here</v-col>
      </v-row>
    </v-card-text>
  </v-card>
</template>

<script>
export default {
  name: "DropZone",
  data() {
    return {
      isActive: false,
    };
  },
  methods: {
    toggleActive() {
      this.isActive = !this.isActive;
    },
    passToParent(event) {
      console.log("ddddd", event.dataTransfer.files[0]);
      this.$emit("on-drop", event);
    },
  },
};
</script>

<style scoped lang="scss">
.drop-zone {
  background-color: #f6f8fb;
  overflow: hidden;
  position: relative;
  &::before {
    content: "";
    position: absolute;
    border: 10px dashed #97bef4;
    border-radius: 15px;
    top: -8px;
    bottom: -8px;
    left: -8px;
    right: -8px;
  }

  &.active {
    background-color: #1976d2;
    color: #fff !important;
    &::before {
      border: 10px dashed #97bef4;
    }
  }
}
</style>
