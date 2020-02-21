<template>
  <div>
    <div class="container" v-for="crypto in cryptos" v-bind:key="crypto.id">
      <h1>{{crypto.currency}}</h1>
      <img width="100px" height="100px" v-bind:src="crypto.logo_url" />
      <h2>{{crypto.price}}</h2>
    </div>
    <div class="container-2">
      <!-- card  -->
      <div class="reddit-card-container">
        <RedditCard v-bind:redditNews="redditNews"/>
      </div>
      <!-- about Chain Link -->
      <div class="chainlink-about">
        <ChainLink v-bind:cryptos="cryptos" mx-auto/>
      </div>
    </div>
  </div>
</template>

<script>
import axios from 'axios'
import RedditCard from '@/components/RedditCard'
import ChainLink from '@/components/ChainLink'

export default {
  components: {
    RedditCard,
    ChainLink
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
      console.log(this.cryptos)
    } catch (error) {
      console.log(error);
    }

    try {
      const linkNews = await axios.get(`https://cryptocontrol.io/api/v1/public/reddit/coin/chainlink?key=${process.env.newsId}`);
      this.redditNews = linkNews.data
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

.container-2{
  display: flex;
}

.chainlink-about{
  background: #3a4660;
  height: 75vh;
  width: 52%;
  margin: 20px 0 10px 20px;
}

</style>
