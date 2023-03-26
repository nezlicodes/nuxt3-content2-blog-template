<template>
  <footer class="full-w full-h">
    <div class="center full-h">
      <span>{{ new Date().getFullYear() }}</span>
    </div>
  </footer>
</template>

<script>
export default {};
</script>

<style  scoped>
footer {
  height: 80px;
  background-color: var(--primary-color);
  color: var(--secondary-color);
}
</style>