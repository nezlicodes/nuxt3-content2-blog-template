
<template>
  <div class="mx-auto container">
    <header class=" my-3 flex p-3 flex-col items-center justify-center bg-gray-100">
  <h1 class="text-4xl font-bold mb-4">Everything Jamstack, AI, electronics</h1>
  <p class="text-lg text-gray-600 mb-8">Get the latest insights and trends on Jamstack, AI, Indie-Makers, electronics, bioinformatics and much more</p>
</header>


    <main class="max-w-5xl mx-auto px-3">
      <section class="page-section">
        <ContentList
          path="/blog"
          :query="{
            only: ['title', 'description', 'tags', '_path', 'img'],
            where: {
              tags: {
                $contains: filter,
              },
            },
            $sensitivity: 'base',
          }"
        >
          <!-- Default list slot -->
          <template v-slot="{ list }">
            <ul class="divide-y divide-gray-200">
              <li v-for="article in list" :key="article._path" class="py-6">
                <NuxtLink :to="article._path" class="block">
                  <div class="flex items-center gap-5">
                    <div class="flex-shrink-0">
                      <span class="text-5xl">&#x1F4D5;</span>
                    </div>
                    <div class="ml- my-20">
                      <h2 class="text-xl font-bold text-gray-900">
                        {{ article.title }}
                      </h2>
                      <p class="text-base text-center text-gray-500">
                        {{ article.description }}
                      </p>
                      <ul class="mt-2">
                        <li
                          v-for="(tag, n) in article.tags"
                          :key="n"
                          class="inline-block bg-gray-200 text-gray-700 text-xs py-0.5 px-1 rounded-full mr-2 mt-2"
                        >
                          {{ tag }}
                        </li>
                      </ul>
                    </div>
                  </div>
                </NuxtLink>
              </li>
            </ul>
          </template>

          <!-- Not found slot to display message when no content us is found -->
          <template #not-found>
            <p>No articles found.</p>
          </template>
        </ContentList>
      </section>
    </main>
  </div>
</template>
  
  
  <script setup>
definePageMeta({
  key: (route) => route.fullPath,
});

// get tag query
const {
  query: { tags },
} = useRoute();

const filter = ref(tags?.split(","));

// set meta for page
useHead({
  title: "",
  meta: [
    { name: "description", content: "Here's a list of all my great articles" },
  ],
});
</script>
  
  
  <style  scoped>
.container {
  min-height: 100%;
  min-width: 100%;
}
.article {
  margin: 50px 0;
}

.title {
  display: block;
  text-align: center;
  margin: 10px 0;
  color: var(--primary-color);
}

button.link {
  margin-bottom: 20px;
  font-size: 1.2rem;
  color: var(--secondary-color);
  background-color: var(--primary-color);
  padding: 5px 10px;
  border-radius: 5px;
  transition: color 500ms cubic-bezier(0.23, 1, 0.32, 1);
}

button.link:hover {
  background-color: var(--secondary-color);
  color: var(--primary-color);
  transition: background-color 500ms cubic-bezier(0.23, 1, 0.32, 1),
    color 500ms cubic-bezier(0.25, 0.46, 0.45, 0.94);
}

.button-link:hover {
  text-decoration: none;
}
p {
  text-align: justify;
  padding: 10px 0 0 0;
}

ul {
  max-width: 900px;
}

.date {
  color: var(--meta-text-color);
}
header{
    min-height: 300px;
}
</style>