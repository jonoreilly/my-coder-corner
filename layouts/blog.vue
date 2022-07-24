<template>
  <NuxtLayout name="default">
    <div class="md:flex">
      <nav>
        <ContentNavigation v-slot="{ navigation }">
          <NavigationTree :navigation="navigation" />
        </ContentNavigation>
      </nav>

      <slot></slot>
    </div>
  </NuxtLayout>
</template>

<script setup lang="ts">
import NavigationTree from "@/components/layouts/header/navigation/Tree.vue";
</script>
