<template>
  <div>
    <div class="article">
      <div class="flex jc-center">
        <ul class="jc-center flex full-w">
          <!-- <li v-for="tag in tags" :key="tag">
            <nuxt-link class="primary-link" :to="`/blog/tag/${getTag(tag)}`">
              #{{ tag }}</nuxt-link
            >
          </li> -->
        </ul>
      </div>

      <h1 class="primary-text text-center">{{ title }}</h1>
      <div class="center">
        <p class="flex date">
          <font-awesome-icon :icon="['fa', 'calendar']" />{{ date }}
        </p>
      </div>
    </div>
  </div>
</template>
  
  <script>
export default {
  props: ["tags", "name", "title", "date"],
};
</script>
  
  <style  scoped>
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
</style>