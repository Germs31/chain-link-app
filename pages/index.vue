<template>
  <div>
    <div class="container" v-for="crypto in cryptos" v-bind:key="crypto.id">
      <h1>{{crypto.currency}}</h1>
      <img width="100px" height="100px" v-bind:src="crypto.logo_url" />
      <h2>{{crypto.price}}</h2>
    </div>
    <!-- card  -->
    <div class="reddit-card-container">
      <RedditCard v-bind:redditNews="redditNews"/>
    </div>
  </div>
</template>

<script>
import axios from 'axios'
import RedditCard from '@/components/RedditCard'

export default {
  components: {
    RedditCard
  },
  data(){
    return {
      cryptos: [],
      redditNews: [],
    }
  },
  async created() {
    try {
      const cryptoCur = await axios.get(`https://api.nomics.com/v1/currencies/ticker?key=${process.env.cryptId}&ids=LINK`);

      this.cryptos = cryptoCur.data
      // console.log(this.cryptos)

    } catch (error) {
      console.log(error);
    }

    try {
      const linkNews = await axios.get(`https://cryptocontrol.io/api/v1/public/reddit/coin/chainlink?key=${process.env.newsId}`);
      // console.log(linkNews)
      this.redditNews = linkNews.data
      console.log(this.redditNews)
    } catch (error) {
      console.log(error)
    }
  }
}
</script>

<style>
.container{
  height: 25vh;
  background: #3a4660;
  display: flex;
  justify-content: space-around;
  align-items: center;
}
</style>
