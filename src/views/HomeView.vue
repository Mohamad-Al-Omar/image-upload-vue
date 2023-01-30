<template>
  <v-container fluid>
    <v-row justify="center">
      <v-col cols="12" sm="8" md="6">
        <v-card>
          <v-card-title class="justify-center text-h5 text-md-h3">
            Upload your image
          </v-card-title>
          <v-card-subtitle class="text-center text-h6 mt-3">
            File should be Jpeg, Png ...
          </v-card-subtitle>
          <v-card-text>
            <v-row>
              <v-col cols="12">
                <drop-zone @on-drop="drop" />
              </v-col>
              <v-col cols="12" class="text-center"> <div>Or</div></v-col>
              <v-col cols="12" class="text-center">
                <file-input></file-input>
              </v-col>
            </v-row>
          </v-card-text>
        </v-card>
      </v-col>
    </v-row>
  </v-container>
</template>

<script>
import DropZone from "@/components/draggable/drop-zone.vue";
import FileInput from "../components/inputs/file-input.vue";
export default {
  name: "HomeView",
  components: {
    DropZone,
    FileInput,
  },
  methods: {
    drop(event) {
      console.log("event => ", event);
    },
  },
};
</script>
<style scoped lang="scss">
.container {
  min-height: 100vh;
  background: #fafafb;
  display: flex;
  justify-content: center;
  align-items: center;
}
</style>
