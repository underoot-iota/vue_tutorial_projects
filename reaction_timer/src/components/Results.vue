<template>
  <p>Reaction Time : {{ score }} ms</p>
  <p class="rank">{{ rank }}</p>
</template>

<script>
export default {
    props: ['score'],
    data(){
        return{
            rank: null
        }
    },
    mounted(){
        if(this.score < 200){
            this.rank = 'S1mple'
        } else if(this.score < 250){
            this.rank = 'Niko'
        } else if(this.score < 300){
            this.rank = 'Rain'
        }else if(this.score < 350){
            this.rank = 'Zywoo'
        } else{
            this.rank = 'Fffsss'
        }
    }
}
</script>

<style>
    .rank{
        font-size: 1.4rem;
        color: #0faf87;
        font-weight: bold;
    }
</style>