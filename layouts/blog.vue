<template>
  <NuxtLayout name="default">
    <div class="min-h-screen grid grid-cols-[1fr_auto_1fr]">
      <div class="sticky top-0 max-h-screen overflow-y-scroll">
        <nav class="p-3 h-full w-60 bg-green-50">
          <ContentNavigation v-slot="{ navigation }">
            <NavigationTree :navigation="navigation" />
          </ContentNavigation>
        </nav>
      </div>

      <div class="max-w-2xl w-screen">
        <slot></slot>
      </div>

      <div></div>
    </div>
  </NuxtLayout>
</template>

<script setup lang="ts">
import NavigationTree from "@/components/layouts/header/navigation/Tree.vue";
</script>
