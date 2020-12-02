<template>
  <div>
    <Header />
    <div class="wrapper">
      <Nuxt />
    </div>
  </div>
</template>

<script lang="ts">
import Vue from "vue";
import Header from "~/components/organisms/Header.vue";
export default Vue.extend({
  components: {
    Header
  }
});
</script>

<style lang="scss" scoped></style>
