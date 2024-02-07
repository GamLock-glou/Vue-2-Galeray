<template>
  <v-col cols="4">
    <v-card @click="openPhoto">
      <v-card-title>
        {{ photo.title }}
      </v-card-title>
      <v-btn v-on:click="clickDeletePhoto">Delete</v-btn>
      <v-card-text>
        <v-img
          width="200"
          height="200"
          :src="photo.url"
        />
      </v-card-text>
    </v-card>
  </v-col>
</template>

<script>

import {mapMutations} from "vuex";

export default {
  props: {
    photo: {
      type: Object,
      required: true
    }
  },
  name: "Photo",
  methods: {
    ...mapMutations(["setCurrentPhoto", "showDialog", "hideDialog", "deletePhoto"]),
    openPhoto() {
      this.setCurrentPhoto(this.photo);
      this.showDialog();
    },
    clickDeletePhoto(e) {
      e.stopPropagation();
      this.deletePhoto(this.photo.id)
    }
  }
}

</script>
