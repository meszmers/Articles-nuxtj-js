<template >
  <div class="article">
      <section v-for="(article, index) in articles" :key="index">
        <h2>{{ article.headline }}</h2>
        <img class="image" :src="article.media[0].sources.landscape.large">

      </section>
  </div>
</template>

<script>
export default {
  data() {
    return {
      articles: []
    }
  },
  async fetch() {
    this.articles = await fetch(
      'https://services.postimees.ee/rest/v1/sections/81/editorsChoice/articles?limit=5'
    ).then(res => res.json())
  }
}
</script>

<style>
.image {
  text-align: right;
  width: 780px;
}
.article {
  margin-left: 100px;
}
</style>
