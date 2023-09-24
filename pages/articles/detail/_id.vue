<template>
  <div class="container py-4">
    <h2>acticle id: {{ this.$route.params.id }}</h2>
    <div class="row" v-for="(article, i) in articles" :key="i">
      <div v-if="article.id == paramId" class="card" style="width: 18rem">
        <img :src="article.img" class="card-img-top" :alt="article.title" />
        <div class="card-body">
          <h5 class="card-title">{{ article.title }}</h5>
          <p class="card-text">{{ article.content }}</p>
          <div
            class="btn btn-outline-secondary btn-sm mb-3"
            @click="$router.go(-1)"
          >
            Kembali
          </div>
        </div>
      </div>
    </div>
  </div>
</template>
<script>
export default {
  data() {
    return {
      paramId: this.$route.params.id,
      articles: [
        {
          id: 1,
          title: 'Judul Artikel 1',
          content:
            'Lorem ipsum dolor sit amet, consectetur adipisicing elit. Placeat dolor explicabo sint quos exercitationem fugiat reiciendis assumenda. Ad quia veritatis, dolor odit, voluptas numquam modi porro eius reprehenderit ullam tenetur?',
          img: 'https://images.unsplash.com/photo-1649282806617-c51bb282899c?ixlib=rb-1.2.1&ixid=MnwxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8&auto=format&fit=crop&w=2070&q=80',
        },
        {
          id: 2,
          title: 'Judul Artikel 2',
          content:
            'Lorem ipsum dolor sit amet, consectetur adipisicing elit. Placeat dolor explicabo sint quos exercitationem fugiat reiciendis assumenda. Ad quia veritatis, dolor odit, voluptas numquam modi porro eius reprehenderit ullam tenetur?',
          img: 'https://images.unsplash.com/photo-1635732646038-0a1a2fe3f2d6?ixlib=rb-1.2.1&ixid=MnwxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8&auto=format&fit=crop&w=1074&q=80',
        },
        {
          id: 3,
          title: 'Judul Artikel 3',
          content:
            'Lorem ipsum dolor sit amet, consectetur adipisicing elit. Placeat dolor explicabo sint quos exercitationem fugiat reiciendis assumenda. Ad quia veritatis, dolor odit, voluptas numquam modi porro eius reprehenderit ullam tenetur?',
          img: 'https://images.unsplash.com/photo-1640006807976-a6127e9d6fa0?ixlib=rb-1.2.1&ixid=MnwxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8&auto=format&fit=crop&w=1171&q=80',
        },
      ],
    }
  },
}
</script>
