<template>
  <div>
    <app-store-grid :data="food" />
  </div>
</template>

<script>
import { mapGetters } from "vuex";
import AppStoreGrid from "~/components/AppStoreGrid.vue";

export default {
  components: {
    AppStoreGrid
  },
  computed: {
    ...mapGetters(["food"])
  }
};
</script>

<style lang="scss" scoped>
</style>