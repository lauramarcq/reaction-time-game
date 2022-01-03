<template>
    <div>
        <p>Reaction Time Score: {{score}}</p>
        <p :class="(this.score <= 500)?'rank':'low-rank'">{{rank}}</p>
    </div>
   
</template>

<script>
export default {
    props : ['score'],
    data() {
        return {
            rank: null
        }
    },
    mounted() {
        if (this.score < 250) {
            this.rank = 'Ninja fingers!'
        } else if (this.score < 500) {
            this.rank = 'Rapid reflexes'
        } else if (this.rank < 700) {
            this.rank = 'OMG so slow...'
        }
    }, 
}
</script>

<style>

.rank {
    font-size: 1.4em;
    color: green;
    font-weight: bold;
}
.low-rank {
    font-size: 1.4em;
    color: red;
    font-weight: bold;
}

</style>