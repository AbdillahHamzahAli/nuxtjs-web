<template>
  <div class="container my-5">
    <div class="text-center rounded-3">
      <img
        :src="require(`~/assets/img/books.png`)"
        alt="Logo"
        width="80"
        height="80"
        class="align-text-top"
      />
      <h1 class="text-body-emphasis">We Library</h1>
      <p class="col-lg-8 mx-auto fs-5 text-muted">
        Temukan dunia buku melalui mata kesimpulan kami. Kami menghubungkan Anda
        dengan hikmah dan keindahan dari setiap buku. Mari bersama-sama
        menjelajahi halaman demi halaman pengetahuan dan imajinasi.
      </p>
      <div class="d-inline-flex gap-2 mb-5">
        <button
          class="btn btn-outline-secondary btn-lg px-4 rounded-pill"
          type="button"
        >
          We Books
        </button>
      </div>
    </div>
  </div>
</template>
<script>
export default {}
</script>
<style>
@font-face {
  font-family: 'DM Sans';
  font-style: normal;
  font-weight: 400;
  font-display: swap;
  src: url('~assets/fonts/DMSans-Regular.ttf') format('truetype');
}
</style>
