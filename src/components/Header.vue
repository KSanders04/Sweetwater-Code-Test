<script setup lang="ts">
import sweetwaterLogo from "../assets/sweetwater-logo.svg";
</script>

<template>
  <section>
    <div>
      <img :src="sweetwaterLogo" class="logo" alt="Sweetwater Logo" />
    </div>
  </section>
</template>

<style scoped>
.logo {
  height: 200px;
  width: 200px;
}
</style>
