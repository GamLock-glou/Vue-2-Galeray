<template>
  <v-dialog @click:outside="hideDialog" @keydown.esc="hideDialog" v-model="$store.getters.getDialogVisible" max-width="600">
    <v-card>
      <v-card-title>{{ fullTitle }}</v-card-title>
      <v-card-text>
        <v-img :src="$store.getters.getCurrentPhoto.url" />
      </v-card-text>
    </v-card>
  </v-dialog>
</template>

<script>
import { mapMutations } from 'vuex';
export default {
  name: "PhotoDialog",
  data: () => ({
  }),
  methods: {
    ...mapMutations(['hideDialog'])
  },
  computed: {
    fullTitle() {
      return `Name photo - ${this.$store.getters.getCurrentPhoto.title}`
    }
  }
}
</script>