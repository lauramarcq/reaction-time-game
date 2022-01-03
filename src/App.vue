<template>
  <h1>{{ title }}</h1>
  <input type="text" ref="name">
  <button @click="handleClick">click me</button>

  <div v-if="showModal">
    <modal theme="sale" @close="toggleModal"> 
      <h1>Here is your bargain</h1>
      <p>Grab your bargain now!</p>
    </modal>
  </div>

  <div v-if="showModal2">
    <modal @close="toggleModal2"> 
      <h1>This is modal2</h1>
      <p>GThis is working!</p>
    </modal>
  </div>
  <button @click="toggleModal">Show Sale</button>
  <button @click="toggleModal2">Show another thing</button>

  <h1>Ninja Game</h1>
  <button @click="startNinja" :disabled="isPlaying" class="button-game"> Click Here to Play </button>
  <p>Watch out for the green box and click on it as fast as you can</p>
  <block v-if="isPlaying" :delay="delay" @end="endGame"></block>
  <results v-if="showResults" :score="score"></results>
 


  
</template>

<script>
// import HelloWorld from './components/HelloWorld.vue'
import modal from './components/modal.vue';
import block from './components/block.vue';
import results from './components/results.vue';


export default {
  name: 'App',
  components: { modal, block, results },
  data() {
    return {
      title: "My first Vue App!!",
      showModal: false,
      showModal2: false,
      greenBox: false,
      isPlaying: false,
      delay: null,
      score: null,
      showResults: false
    }
  },
  methods: {
    handleClick () {
      console.log(this.$refs.name)
      this.$refs.name.classList.add('active')
      this.$refs.name.focus()
    },
    toggleModal () {
    this.showModal = !this.showModal
    },
    toggleModal2 () {
    this.showModal2 = !this.showModal2
    },
    startNinja () {
      console.log('it worked')
      this.isPlaying = true
      this.delay = 2000 + Math.random() * 5000
      console.log(this.delay)
      this.showResults = false
    }, 
    endGame(reactionTime) {
      this.score = reactionTime
      this.isPlaying = false
      this.showResults = true
    }
}

}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
.button-game{
  background: #0faf87;
  color: white;
  border: none;
  padding: 8px 16px;
  border-radius: 4px;
  font-size: 16px;
  letter-spacing: 1px;
  cursor: pointer;
  margin: 10px;
}
.button-game[disabled] {
  opacity: 0.2;
  cursor: not-allowed;
}
</style>
