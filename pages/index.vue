<template>
  <div>
    <div  v-for="crypto in cryptos" v-bind:key="crypto.id">
      <img width="100px" height="100px" v-bind:src="crypto.logo_url" />
      <h1>{{crypto.currency}}</h1>
      <h2>{{crypto.price}}</h2>
    </div>
  </div>
</template>

<script>
import axios from 'axios'
export default {
 data(){
   return {
     cryptos: [],
     title: 'hello'
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
 }
}
</script>
