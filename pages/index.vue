<template>
<div>
  <v-card v-for="article in articles" :key="article.slug" class="my-5">
    <v-card-title>{{ article.title }}</v-card-title>
    <v-card-subtitle>{{ moment(article.created_at).format("YYYY/MM/DD")}}</v-card-subtitle>
    <v-card-text>{{ article.description }}</v-card-text>
    <v-card-actions>
      <nuxt-link :to="'/articles/' + article.slug">
        <p>Read more →</p>
      </nuxt-link>
      <v-spacer></v-spacer>
    </v-card-actions>
  </v-card>
</div>
</template>

<script>
import moment from "moment";

export default {
    async asyncData({ $content, params }) {
        const articles = await $content('articles', params.slug)
            .fetch();
        return {
            articles
        }
    },
     data: () => ({
        moment: moment
     })
}
</script>
