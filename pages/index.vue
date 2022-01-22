<template>
<div>
  <h2>POSTS</h2>
  <v-card v-for="article in articles" :key="article.slug" class="my-5">
    <v-card-subtitle>{{ moment(article.created_at).format("YYYY/MM/DD")}}</v-card-subtitle>
    <v-card-actions>
      <nuxt-link :to="'/articles/' + article.slug">
        <p>{{ article.title }}</p>
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
