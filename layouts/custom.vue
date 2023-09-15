<template>
  <div>
    <HeaderWeb />
    <h1 class="text-center P-2">CUSTOM LAYOUT</h1>
    <Nuxt />
  </div>
</template>

<script>
import HeaderWeb from '@/components/HeaderWeb.vue'
export default {
  components: {
    HeaderWeb,
  },
}
</script>
