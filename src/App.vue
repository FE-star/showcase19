<script>
import HelloWorld from './components/HelloWorld.vue'
export default {
  data() {
    return {
      current: 'HelloWorld'
    }
  },
  components: {
    HelloWorld,
  },
  methods: {
    onClick() {
      import('./components/Async.vue')
        .then(Async => {
          this.$.components.Async = Async.default
          this.current = 'Async'
        })
    }
  }
}
</script>

<template>
  <main>
    <component :is="current" msg="You did it!" />
    <button @click="onClick">load async component</button>
  </main>
</template>

<style scoped>
header {
  line-height: 1.5;
}

.logo {
  display: block;
  margin: 0 auto 2rem;
}

@media (min-width: 1024px) {
  header {
    display: flex;
    place-items: center;
    padding-right: calc(var(--section-gap) / 2);
  }

  .logo {
    margin: 0 2rem 0 0;
  }

  header .wrapper {
    display: flex;
    place-items: flex-start;
    flex-wrap: wrap;
  }
}
</style>
