<template>
  <div class="toc">
    <nav>
      <h2 class="mb-2 font-bold text-gray-700 uppercase tracking-wider text-sm">
        Table of Contents
      </h2>
      <div>
        <ul v-if="toc && toc.links">
          <li v-for="link in toc.links" :key="link.text">
            <a :href="`#${link.id}`">
              {{ link.text }}
            </a>
          </li>
        </ul>
      </div>
    </nav>
  </div>
</template>
  
  <script>
const { toc } = useContent();
</script>
  
  <style>
/* Optional styles for the TOC component */
.toc {
  max-height: 80vh;
  overflow-y: auto;
  scrollbar-width: thin;
  scrollbar-color: rgba(209, 213, 219, var(--tw-scrollbar-opacity)) transparent;
}

.toc::-webkit-scrollbar {
  width: 6px;
}

.toc::-webkit-scrollbar-thumb {
  background-color: rgba(209, 213, 219, var(--tw-scrollbar-opacity));
  border-radius: 3px;
}
</style>
  