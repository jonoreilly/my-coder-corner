<template>
  <div class="border rounded">
    <div class="border flex px-2 gap-2">
      <div>
        {{ language }}
      </div>

      <div>
        {{ filename }}
      </div>

      <div class="ml-auto">
        <button @click="copy()">Copy</button>
      </div>
    </div>

    <div class="container p-4 overflow-scroll">
      <slot />
    </div>
  </div>
</template>

<script setup lang="ts">
const props = withDefaults(
  defineProps<{
    code?: string;
    language?: string | null;
    filename?: string | null;
    highlights?: number[];
  }>(),
  { code: "", language: null, filename: null, highlights: null }
);

function copy() {
  navigator.clipboard.writeText(props.code);
}
</script>
