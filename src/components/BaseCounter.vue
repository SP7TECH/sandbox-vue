<script>
export default {
  data() {
    return {
      counterTitle: 'Counter Standard',
      count: 10,
      incrementAmount: 1,
    }
  },
  computed: {
    displayTitle() {
      if (this.count > 20) {
        return 'Counter Standard - Very Long'
      } else {
        return 'Counter Standard'
      }
    },
    optimizedIncrementAmount() {
      return this.displayTitle.length * this.incrementAmount
    },
  },
  methods: {
    increment(amount, event) {
      console.log(amount, event)
    },
    incrementCount() {
      this.count += this.incrementAmount
    },
    changeIncrementCount(event) {
      this.incrementAmount = Number(event.target.value)
    },
  },
}
</script>

<template>
  <h1>{{ displayTitle }}</h1>

  <h3>Count - {{ count }}</h3>
  <h3>Optimized Count - {{ optimizedIncrementAmount }}</h3>

  <h4>{{ incrementAmount }}</h4>
  <div>
    <label for="incCount">Increment Count</label>
    <input type="number" v-bind:value="incrementAmount" v-on:input="changeIncrementCount" />
  </div>

  <div>
    <label for="incCount">Increment Count</label>
    <input type="number" v-model="incrementAmount" />
  </div>

  <button v-on:click="incrementCount">Increment Count</button>
  <button v-on:click="increment(10, $event)">Increment Count</button>
</template>
