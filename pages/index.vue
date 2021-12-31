<template>
<div>
  <div v-for="article in articles" :key="article.slug">
    {{ moment(article.created_at).format("YYYY/MM/DD")}}
    <nuxt-link :to="'/articles/' + article.slug">
      <h3>{{ article.title }}</h3>
    </nuxt-link>
    <p>{{ article.description }}</p>
    <hr style="border:0;border-top:1px solid">
  </div>
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
