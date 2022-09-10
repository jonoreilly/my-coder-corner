<template>
  <main>
    <article class="my-5 mx-4">
      <!-- TODO: investigate paths -->
      <ContentDoc :path="blogPath" class="blog" />

      <Author />
    </article>
  </main>
</template>

<script setup lang="ts">
import Author from "@/components/blogs/Author.vue";

definePageMeta({
  layout: "blog",
});

const route = useRoute();

const slug = route.params.slug;

const blogPath = "/blogs/" + ((slug.length ? slug : []) as string[]).join("/");

// TODO: Add json ld to blogs

// const jsonLd = `{"@context":"https://schema.org","@graph":[{"@type":"WebSite","@id":"https://blog.logrocket.com/#website","url":"https://blog.logrocket.com/","name":"LogRocket Blog","description":"For Frontend Developers and Web App Engineers","potentialAction":[{"@type":"SearchAction","target":{"@type":"EntryPoint","urlTemplate":"https://blog.logrocket.com/?s={search_term_string}"},"query-input":"required name=search_term_string"}],"inLanguage":"en-US"},{"@type":"ImageObject","inLanguage":"en-US","@id":"https://blog.logrocket.com/managing-full-stack-monorepo-pnpm/#primaryimage","url":"https://blog.logrocket.com/wp-content/uploads/2022/07/creating-full-stack-multi-package-monorepo-using-pnpm-nocdn.png","contentUrl":"https://blog.logrocket.com/wp-content/uploads/2022/07/creating-full-stack-multi-package-monorepo-using-pnpm-nocdn.png","width":730,"height":487,"caption":"Managing a fullstack multi-package monorepo using pnpm"},{"@type":"WebPage","@id":"https://blog.logrocket.com/managing-full-stack-monorepo-pnpm/","url":"https://blog.logrocket.com/managing-full-stack-monorepo-pnpm/","name":"Managing a full-stack, multipackage monorepo using pnpm - LogRocket Blog","isPartOf":{"@id":"https://blog.logrocket.com/#website"},"primaryImageOfPage":{"@id":"https://blog.logrocket.com/managing-full-stack-monorepo-pnpm/#primaryimage"},"datePublished":"2022-07-20T13:00:41+00:00","dateModified":"2022-07-22T14:33:49+00:00","author":{"@id":"https://blog.logrocket.com/#/schema/person/7aa515ca0a4441d14dedcf3869cc52d4"},"description":"Learn why pnpm performs better than npm and how the many special workspaces features make it ideal for managing a multi-package monorepo.","breadcrumb":{"@id":"https://blog.logrocket.com/managing-full-stack-monorepo-pnpm/#breadcrumb"},"inLanguage":"en-US","potentialAction":[{"@type":"ReadAction","target":["https://blog.logrocket.com/managing-full-stack-monorepo-pnpm/"]}]},{"@type":"BreadcrumbList","@id":"https://blog.logrocket.com/managing-full-stack-monorepo-pnpm/#breadcrumb","itemListElement":[{"@type":"ListItem","position":1,"name":"Home","item":"https://blog.logrocket.com/"},{"@type":"ListItem","position":2,"name":"Managing a full-stack, multipackage monorepo using pnpm"}]},{"@type":"Person","@id":"https://blog.logrocket.com/#/schema/person/7aa515ca0a4441d14dedcf3869cc52d4","name":"Ashley Davis","image":{"@type":"ImageObject","inLanguage":"en-US","@id":"https://blog.logrocket.com/#/schema/person/image/","url":"https://secure.gravatar.com/avatar/a9d0d14739a1379e6b8233109fc0e158?s=96&d=mm&r=g","contentUrl":"https://secure.gravatar.com/avatar/a9d0d14739a1379e6b8233109fc0e158?s=96&d=mm&r=g","caption":"Ashley Davis"},"description":"Ashley Davis is an experienced software developer and author. He is CTO of Sortal and helps businesses manage their digital assets using machine learning.","sameAs":["http://www.the-data-wrangler.com/","https://twitter.com/https://twitter.com/ashleydavis75"],"url":"https://blog.logrocket.com/author/ashleydavis/"}]}`;

// useHead({
//   script: [
//     {
//       type: "application/ld+json",
//       children: JSON.stringify(jsonLd),
//     },
//   ],
// });
</script>

<style scoped lang="postcss">
:deep(.blog) {
  h1 {
    @apply text-3xl;
  }

  p {
    @apply my-3;
  }
}
</style>
