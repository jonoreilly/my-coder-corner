<template>
  <div class="pl-2">
    <!-- This level -->

    <NuxtLink :to="entry._path">
      {{ entry.title }}
    </NuxtLink>

    <!-- Children -->
    <ul v-if="children.length">
      <li v-for="child in children">
        <entry :entry="child" />
      </li>
    </ul>
  </div>
</template>

<script setup lang="ts">
import { defineProps } from "vue";
import type { NavItem } from "@nuxt/content/dist/runtime/types";

const props = defineProps<{ entry: NavItem }>();

const children = computed(() => {
  // Group by path
  const childrenMap: Record<string, NavItem> =
    props.entry.children
      // Remove index
      ?.filter((el) => el._path !== props.entry._path)
      // Join duplicates
      .reduce((acc, cur) => {
        if (acc[cur._path]) {
          if (!acc[cur._path].children?.length) {
            acc[cur._path].children = [];
          }

          acc[cur._path].children.push(...cur.children);
        } else {
          acc[cur._path] = cur;
        }

        return acc;
      }, {}) ?? {};

  // Revert to array
  return Object.values(childrenMap);
});
</script>

<style scoped>
.router-link-active {
  @apply underline;
}
</style>
