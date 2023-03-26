<template>
<main id="main" class="max-w-7xl mx-auto px-4">
    <header v-if="data.article" class="mt-12">
      <div class="mb-8 ">
      <span  style="font-size: 5rem;"> 📕</span> 
      </div>
      <h1 class="text-3xl font-bold mb-2">{{ data.article.title }}</h1>
      <p class="text-lg text-gray-600 mb-4">{{ data.article.description }}</p>
      <ul class="flex flex-wrap mb-6">
        <li
          class="bg-gray-200 text-gray-700 rounded-full py-1 px-2 text-sm mr-2 mb-2"
          v-for="(tag, n) in data.article.tags"
          :key="n"
        >
          {{ tag }}
        </li>
      </ul>
    </header>
    <hr class="my-12" />
    <section class="flex flex-wrap items-start justify-between">
      <aside class="w-full md:w-1/4">
        <!-- Toc Component -->
        <h2 class="mb-2 font-bold text-gray-700 uppercase tracking-wider text-sm">
          Table of Contents
        </h2>
        <div>
          <ul v-if="toc && toc.links">
            <li v-for="link in toc.links" :key="link.text">
              <a :href="`#${link.id}`" class="text-gray-600 hover:text-gray-900">
                {{ link.text }}
              </a>
            </li>
          </ul>
        </div>
        <hr class="md:hidden my-5"/>
      </aside>
      <article class="prose prose-lg w-full md:w-3/4">
        <!-- render document coming from query -->
        <ContentRenderer :value="data.article">
          <!-- render rich text from document
          <MarkdownRenderer :value="data.article" /> -->

          <!-- display if document content is empty -->
          <template #empty>
            <p>No content found.</p>
          </template>
        </ContentRenderer>
      </article>
    </section>

    <!-- PrevNext Component -->
    <PrevNext :prev="prev" :next="next" class="my-12" />
  </main>

</template>

<script setup>
const { path } = useRoute();
const { toc } = useContent();
const { data } = await useAsyncData(`content-${path}`, async () => {
  // fetch document where the document path matches with the cuurent route
  let article = queryContent().where({ _path: path }).findOne();
  // get the surround information,
  // which is an array of documeents that come before and after the current document
  let surround = queryContent()
    .only(["_path", "title", "description"])
    .sort({ date: 1 })
    .findSurround(path);

  return {
    article: await article,
    surround: await surround,
  };
});

// destrucure `prev` and `next` value from data
const [prev, next] = data.value.surround;
console.log({ data, prev, next });

// set the meta
useHead({
  title: data.value.article.title,
  meta: [
    { name: "description", content: data.value.article.description },
    {
      hid: "og:image",
      property: "og:image",
      content: `https://blog.lylianezli.com/${data.value.article.img}`,
    },
  ],
});
</script>
<style lang="pcss" scoped>
.img-cont {
  overflow: hidden;
  height: 350px;
}
img {
  width: 100%;
  height: auto;
  overflow: hidden;
  background-position: center;
}
</style>