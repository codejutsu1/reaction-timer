<template>
  <div>
    <p>Reaction Time: {{ score }} ms</p>
    <p class="rank">{{ rank }}</p>
  </div>
</template>

<script>
export default {
    props: ['score'],
    data () {
        return {
            rank: null
        }
    },
    mounted() {
        if(this.score == 1){
            this.rank = "You are a god"
        }else if(this.score < 11){
            this.rank = 'You are a demigod'
        }else if(this.score < 200){
            this.rank = 'You are a Legend'
        }else if(this.score < 250){
            this.rank = "Master Reflexes"
        }else if(this.score < 400){
            this.rank = "Rapid Reflexes"
        }else{
            this.rank = 'Snail pace...'
        }
    }
}
</script>

<style>
    .rank{
        font-size: 1.4em;
        color: #0faf87;
        font-weight: bold;
    }
</style>