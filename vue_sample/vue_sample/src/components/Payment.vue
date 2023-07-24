<script setup lang="ts">

const itemName1: string = 'Desk'
const itemName2: string = 'Bike'

const price1: number = 40000
const price2: number = 20000

const url1 = 'https://google.com'

const buy = (itemName: string) => {
  alert('Are you sure to buy ' + itemName + '?')
}

</script>

<template>
  <div class="container">
    <h1>最近の支出</h1>
    <div class="payment">
      <label>{{ itemName1 }}</label>
      <label>{{ price1 }}</label>
      <a :href="url1"> bought at...</a>
      <button @click="buy(itemName1)">BUY</button>
    </div>
    <div class="payment">
      <label>{{ itemName2 }}</label>
      <label>{{ price2 }}</label>
      <button @click="buy(itemName1)">BUY</button>
    </div>
  </div>
</template>

<style scoped>
.container {
  display: flex;
  flex-direction: column;
  align-items: center;
}

.payment {
  display: flex;
  justify-content: space-between;
  align-items: center;
  height: 80px;
  width: 400px;
  background-color: aliceblue;
  margin-bottom: .5em;
}

label {
  font-size: 20px;
}
</style>