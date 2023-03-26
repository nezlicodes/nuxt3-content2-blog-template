<template>
  <header class="full-w full-h">
    <div class="center full-h">
      <p>
        <span class="generated">{{ todo }}</span>
      </p>
    </div>
  </header>
</template>

<script>
export default {
  data() {
    return {
      services: [
        "UX design",
        "Digital nomadism",
        "UI design",
        "rduino",
        "JAMStack",
        "Indie maker",
      ],
      current: "UX",
      counter: 0,
    };
  },
  computed: {
    count: function () {
      setTimeout(() => {
        this.counter =
          this.counter < this.services.length - 1
            ? (this.counter = this.counter + 1)
            : 0;
      }, 1500);
      return this.counter;
    },
    todo: function () {
      return (this.current = this.services[this.count]);
    },
  },
};
</script>

<style scoped>
header {
  height: 300px;
  background-color: var(--primary-color);
  color: var(--secondary-color);
}

p {
  font-size: 30px;
}
</style>
