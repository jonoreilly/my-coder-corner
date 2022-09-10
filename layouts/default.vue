<template>
  <div class="min-h-screen grid grid-rows-[max-content_auto_max-content]">
    <TheHeader />

    <div>
      <slot></slot>
    </div>

    <TheFooter />
  </div>
</template>

<script setup lang="ts">
import TheHeader from "@/components/layouts/header/TheHeader.vue";
import TheFooter from "@/components/layouts/footer/TheFooter.vue";
</script>
