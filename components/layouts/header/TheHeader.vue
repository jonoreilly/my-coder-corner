<template>
  <header>
    <nav>
      <ContentNavigation v-slot="{ navigation }">
        <NavigationTree :navigation="navigation" />
      </ContentNavigation>
    </nav>
  </header>
</template>

<script setup lang="ts">
import NavigationTree from "./navigation/Tree.vue";
</script>
