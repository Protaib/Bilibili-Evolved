<template>
  <div class="simplify-home">
    <component class="simplify-home-component" :is="activeComponent"></component>
  </div>
</template>
<script lang="ts">
export default {
  components: {
    'minimal-home': () => import('./minimal-home/minimal-home.vue'),
    'simple-home': () => import('./simple-home/simple-home.vue'),
  },
  computed: {
    activeComponent () {
      return this.homeStyle === '清爽' ? 'simple-home' : 'minimal-home'
    }
  },
  props: {
    homeStyle: String,
  },
}
</script>
<style lang="scss">
.simplify-home {
  padding: 32px 72px 0;
  display: flex;
  align-items: flex-start;
  justify-content: center;
  min-height: 100vh;
  --simplify-home-background: #f4f4f4;
  background-color: var(--simplify-home-background);
  font-size: 12px;

  body.dark & {
    --simplify-home-background: #181818;
  }
  .simplify-home-component {
    max-width: min(100%, 2000px);
  }
}
html {
  scroll-behavior: smooth;
}
</style>