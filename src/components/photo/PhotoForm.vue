<template>
  <v-container>
    <v-row class="d-flex">
      <v-text-field v-model="title" />
      <v-file-input v-model="img" />
      <v-btn @click="clickAddPhoto">Add</v-btn>
    </v-row>
  </v-container>
</template>

<script>

import {mapMutations} from "vuex";

export default {
  name: "PhotoForm",
  data: () => ({
    title: "",
    img: null,
  }),
  methods: {
    ...mapMutations(["addPhoto"]),
    clickAddPhoto() {
      const reader = new FileReader();
      reader.onload = () => {
        const photo = {
          id: Date.now(),
          title: this.title,
          url: reader.result
        }
        this.addPhoto(photo)
      }
      reader.readAsDataURL(this.img)
    }
  }
}
</script>

