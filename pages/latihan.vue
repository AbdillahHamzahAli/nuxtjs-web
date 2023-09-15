<template>
  <div class="container">
    <!-- <div ref="example-element">{{ counter }}</div> -->
    <div v-if="isLoading" class="spinner-border" role="status">
      <span class="visually-hidden">Loading...</span>
    </div>
    <div v-else>
      <h1 class="text-center">LATIHAN 1</h1>
      <!-- <div ref="example-element">{{ isLoading }}</div> -->
    </div>
  </div>
</template>

<script>
export default {
  layout(context) {
    return 'custom'
  },
  data() {
    return {
      counter: 0,
      property: 'old',
      loading: true,
    }
  },
  computed: {
    isLoading() {
      return this.loading
    },
  },
  created() {
    setTimeout(() => {
      this.loading = false
    }, 3000)
  },
}
</script>
