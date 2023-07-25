<script setup lang="ts">
import { reactive } from 'vue'

// const itemName1 = ref<string>('Desk')
const itemName2: string = 'Bike'

const item1 = reactive({
  name: 'Desk',
  price: 40000
})

// const price1: number = 40000
const price2: number = 20000

const url1 = 'https://google.com'

const buy = (itemName: string) => {
  alert('Are you sure to buy ' + itemName + '?')
}

// v-modelを記述すれば不要
// const input = (e: any) => {
//   item1.name = e.target.value
// }
// const inputPrice = (e: any) => {
//   item1.price = e.target.value
// }

const clear = () => {
  item1.name = 'なし'
  item1.price = 0
}

</script>

<template>
  <div class="container">
    <h1>Payment</h1>
    <input v-model="item1.name" />
    <input v-model="item1.price" />

    <!-- v-modelで記述する際は不要 -->
    <!-- <input @input="input" :value="item1.name" /> -->
    <!-- <input @input="inputPrice" :value="item1.price" /> -->

    <button @click="clear">Clear</button>
    <div class="payment">
      <label>{{ item1.name }}</label>
      <label>{{ item1.price }} yen</label>
      <a :href="url1"> bought at...</a>
      <button @click="buy(item1.name)">BUY</button>
    </div>
    <div class="payment">
      <label>{{ itemName2 }}</label>
      <label>{{ price2 }} yen</label>
      <button @click="buy(itemName2)">BUY</button>
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

input {
  margin-bottom: .7em;
}

label {
  font-size: 20px;
}
</style>