<template>
  <main>
    <article>
      <img
        src="@/assets/media/authors/jon-oreilly.jpeg"
        width="50"
        height="50"
      />

      <h1>Jon O'Reilly</h1>

      <p>Frontend Engineer</p>
    </article>
  </main>
</template>

<script setup lang="ts">
import jsonLd from "@/assets/jsonLd/authors/jon-oreilly.json";

useHead({
  script: [
    {
      type: "application/ld+json",
      children: JSON.stringify(jsonLd),
    },
  ],
});
</script>
