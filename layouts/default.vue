<template>
  <div>
    <TheHeader />

    <slot></slot>

    <TheFooter />
  </div>
</template>

<script setup lang="ts">
import TheHeader from "@/components/layouts/header/TheHeader.vue";
import TheFooter from "@/components/layouts/footer/TheFooter.vue";
</script>
