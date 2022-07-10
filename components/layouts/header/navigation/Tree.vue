<template>
  <ul>
    <li v-for="entry in navigation">
      <Entry :entry="entry" />
    </li>
  </ul>
</template>

<script setup lang="ts">
import type { NavItem } from "@nuxt/content/dist/runtime/types";
import Entry from "./Entry.vue";

const props = defineProps<{ navigation: NavItem[] }>();
</script>
