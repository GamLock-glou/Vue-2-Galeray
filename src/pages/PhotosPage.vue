<template>
  <v-container>
    <PhotoForm v-if="getAllPhotos.length < 11" v-show="!getDialogVisible" />
    <div v-else>Вы больше не можете добавить больше фото</div>
    <v-row>
      <Photo
        v-for="photo in getAllPhotos"
        :photo="photo"
      />
    </v-row>
    <PhotoDialog />
  </v-container>
</template>

<script>

import Photo from "@/components/photo/Photo"
import PhotoForm from "@/components/photo/PhotoForm"
import PhotoDialog from "@/components/photo/PhotoDialog"
import {mapActions, mapGetters} from "vuex";

export default {
  name: "PhotosPage",
  components: {
    Photo,
    PhotoForm,
    PhotoDialog,
  },
  data: () => ({
    photos: [],
  }),
  mounted() {
    this.fetchPhotos()
  },
  methods: {
    ...mapActions(["fetchPhotos"]),
    deletePhoto(id) {
      const newPhotos = this.photos.filter(photo => photo.id !== id);
      this.photos = newPhotos
    }
  },
  computed: {
    ...mapGetters(["getDialogVisible", "getAllPhotos"]),
  }
}

</script>
