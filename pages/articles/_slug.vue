<template>
  <div>
        <div align="center" class="mb-10 mt-10">
           <p> {{ moment(article.created_at).format("YYYY/MM/DD")}} </p>
           <h1> {{article.title}} </h1>
           <hr>
        </div>
        <article>
            <nuxt-content :document="article" />
        </article>
  </div>
</template>

<script>
import moment from "moment";

export default {
    async asyncData({ $content, params }) {
        const article = await $content('articles', params.slug).fetch();
        return { article }
    },
    data: () => ({
       moment: moment
    })
}
</script>
