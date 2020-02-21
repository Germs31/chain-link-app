<template>
  <div>
    <h2>Reddit News Articles</h2>
    <v-flex py-3 v-for="news in redditNews" v-bind:key="news">
        <v-card class="reddit-card" max-width="500" outlined>
            <v-list-item three-line>
                <v-list-item-content>
                    <v-list-item-title class="headline mb-1">{{news.title}}</v-list-item-title>
                    <v-list-item-subtitle>{{news.publishedAt}}</v-list-item-subtitle>

                    <v-card-actions>
                        <v-btn text v-bind:href="news.url" target="_blank">Link</v-btn>
                    </v-card-actions>
                </v-list-item-content>
            </v-list-item>
        </v-card>
    </v-flex>
  </div>
  
</template>

<script>
export default {
    name:"RedditCard",
    props: ['redditNews']
}
console.log()
</script>

<style scooped>
    .reddit-card , h2{
        margin-left: 50px;
    }
</style>