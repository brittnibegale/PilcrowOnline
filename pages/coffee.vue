<template>
  <div>
    <app-store-grid :data="coffee" />
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
    ...mapGetters(["coffee"])
  }
};
</script>

<style lang="scss" scoped>
</style>