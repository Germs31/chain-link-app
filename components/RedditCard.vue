<template>
  <div>
    <div v-for="news in redditNews" v-bind:key="news">
        <h1>{{news.title}}</h1>
    </div>
  </div>
</template>

<script>
export default {
    name:"RedditCard",
    props: ['redditNews']
}
console.log()
</script>

<style>

</style>