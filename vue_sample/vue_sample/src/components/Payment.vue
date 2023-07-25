<script setup lang="ts">
import { onBeforeMount, onMounted, onUpdated, reactive, ref, toRefs, watch } from 'vue'

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

const budget = 50000

// 何らかの計算をして、処理を分岐したいときcomputed
// const priceLabel = computed(() => {
//   if (item1.price > budget * 2) {
//     return 'tooooo expensive'
//   } else if (item1.price > budget) {
//     return 'too expensive'
//   } else {
//     return item1.price + ' yen'
//   }
// })

// watchでcomputedと同様の処理を行う
const priceLabel = ref<string>(item1.price + ' yen')
const { price } =toRefs(item1)
watch(price, () => {
  if (price.value > budget * 2) {
    priceLabel.value = 'tooooo expensive'
    // return 'tooooo expensive'
  } else if (price.value > budget) {
    priceLabel.value = 'too expensive'
    // return 'too expensive'
  } else {
    priceLabel.value = price.value + ' yen'
    // return price.value + ' yen'
  }
})

// computedを使わなくてもメソッドで実行できるが,
// conputedを使うとvueの中でキャッシュをとったりするので動作が最適化される
// const getPriceLabel = () => {
//   if (item1.price > budget * 2) {
//     return 'tooooo expensive'
//   } else if (item1.price > budget) {
//     return 'too expensive'
//   } else {
//     return item1.price + ' yen'
//   }
// }

// ライフサイクルフック
onBeforeMount(() => {
  console.log('before mount')
})

onMounted(() => {
  console.log('mounted')
})

onUpdated(() => {
  console.log('update')
})

</script>

<template>
  <div class="container">
    <h1>Payment</h1>
    <input v-model="item1.name" />
    <input type="number" v-model="item1.price" />

    <!-- v-modelで記述する際は不要 -->
    <!-- <input @input="input" :value="item1.name" /> -->
    <!-- <input @input="inputPrice" :value="item1.price" /> -->

    <button @click="clear">Clear</button>
    <div class="payment">
      <label>{{ item1.name }}</label>
      <!-- 三項演算子 -->
      <!-- <label>{{ item1.price > budget ? 'too expensive...' : item1.price + ' yen' }}</label> -->
      <label>{{ priceLabel }}</label>
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