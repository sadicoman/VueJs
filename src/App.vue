<template>
  <div>
    <MyParagraphe text="Bonjour" color="green"/>
    <MyParagraphe :text="message"/>
    <h1>Counter: {{counter}}</h1>
    <p>{{message}}</p>
    <button @click.prevent="increment">Incrémenter le compteur</button>
    <h2>Counter x2: {{doubledCounter}}</h2>
  </div>
  <button @click="toggleDiv">Afficher la div</button>
  <div class="div" v-if="isDivDisplayed">Une div</div>
  <input type="text" v-model="message">
  <p>{{ message }}</p>
</template>

<script>
import MyParagraphe from './components/MyParagraphe.vue'
import { computed, ref } from 'vue'
export default {
  components: {
    MyParagraphe
  },
  setup () {
    const message = ref('Un beau message oui <3')

    const counter = ref(0)

    const increment = () => {
      counter.value++
    }

    const doubledCounter = computed(() => {
      return counter.value * 2
    })

    const isDivDisplayed = ref(true)

    const toggleDiv = () => {
      isDivDisplayed.value = !isDivDisplayed.value
    }

    return {
      message,
      counter,
      increment,
      doubledCounter,
      isDivDisplayed,
      toggleDiv
    }
  }
}

</script>

<style lang="scss">
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
.div{
  background-color: red;
  min-height: 300px;
}
</style>
