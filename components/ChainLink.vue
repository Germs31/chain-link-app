<template> 
    <div class="chain-about">
        <v-flex v-for="crypto in cryptos" v-bind:key="crypto.id">
            <h1>{{crypto.name}}</h1>
            <p>Market Cap: {{crypto.market_cap}}</p>
            <p>Circulating: {{crypto.circulating_supply}}</p>
            <p>Historically, the blockchains on which smart contracts run cannot support native communication with external systems, and the potential that smart contracts provide have been throttled by their inability to connect off-chain.

            Today, the solution to this problem is to introduce a new functionality, called an oracle, that provides connectivity to the outside world. However, oracles to-date are centralized services, meaning any smart contract using such services has a single point of failure, which nullifies any benefits gained from the decentralized nature of smart contracts.

            To fill this gap, Chainlink was developed as the first decentralized oracle that can provide external data to smart contracts. As a result, the security and determinism of smart contracts can be combined with the knowledge and breadth of real-world external events. Chainlink will provide your smart contract with access to any external API you want to connect your smart contract with, and all the information needed to do so are listed here.</p>
            <v-btn large href="https://chain.link/" target="_blank">Link</v-btn>
        </v-flex> 
    </div>
</template>

<script>
export default {
    name: "ChainLink",
    props: ['cryptos']
}
</script>

<style>
    .chain-about{
        padding: 5%;
    }
</style>