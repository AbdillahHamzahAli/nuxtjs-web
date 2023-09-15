<template>
  <div>
    <button @click="msg = 'Hello'">Ubah Pesan</button>
    <p>{{ msg }}</p>
  </div>
</template>
<script>
export default {
  data() {
    return { msg: '' }
  },
  created() {
    this.msg = 'Hello'
  },
  beforeMount() {
    this.msg = 'Hello World'
  },
  mounted() {
    this.$nextTick(() => {
      this.$nuxt.$loading.start()
      setTimeout(() => this.$nuxt.$loading.finish(), 5000)
    })
  },
  beforeUpdate() {
    this.msg = 'Hello World Again'
  },
}
</script>
