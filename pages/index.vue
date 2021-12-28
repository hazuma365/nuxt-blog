<template>
  <ul>
    <h1>Index Page</h1>
    <li v-for="article in articles" :key="article.slug">
      <nuxt-link :to="'/articles/' + article.slug">
        <h3>{{ article.created_at }} {{ article.title }}</h3>
      </nuxt-link>
      <p>{{ article.description }}</p>
    </li>
  </ul>
</template>

<script>
export default {
    async asyncData({ $content, params }) {
        const articles = await $content('articles', params.slug)
            .fetch();
        return {
            articles
        }
    }
}
</script>
