<template>
  <div>
    <div class="container">

    </div>
  </div>
</template>

<script>
import axios from 'axios'
export default {
 data(){
   return {
     crypto: []
   }
 },
 async created() {
   try {
     const cryptoCur = await axios.get(`https://api.nomics.com/v1/currencies/ticker?key=${process.env.cryptId}&ids=LINK`);

     this.crypto = cryptoCur.data
     console.log(this.crypto)

   } catch (error) {
     console.log(error);
   }
 }
}
</script>
