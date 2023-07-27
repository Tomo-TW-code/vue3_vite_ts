<script setup lang="ts">
import { onMounted, ref } from 'vue';
import axios from 'axios'

const vFocus = {
  mounted: (el: HTMLElement) => {
    el.focus()
  }
}

const userName = ref<string>('')
const interest = ref([])

const data = ref()
const isLoading = ref<boolean>(false)

// GETリクエスト データを取得する
onMounted(async () => {
  isLoading.value = true
  data.value = await axios.get('https://vue-example-6167b-default-rtdb.firebaseio.com/surveys.json')
  isLoading.value = false
  console.log('data is ', data.value)
})

const onSubmit = (e: Event) => {
  
  // backendとの連携の際は、js組み込み関数のfetch()を使う
  // GET:データの取得、　POST：データの作成
  // fetch('https://vue-example-6167b-default-rtdb.firebaseio.com/surveys.json', {
  //   method: 'POST',
  //   headers: {
  //     'Content-Type': 'application/json'
  //   },
  //   // json形式で送る
  //   body: JSON.stringify({
  //     name: userName.value,
  //     interest: interest.value
  //   })
  // })

  // axiosを使うと、簡単にbackendとの連携ができる
  axios.post('https://vue-example-6167b-default-rtdb.firebaseio.com/surveys.json', {
    name: userName.value,
    interest: interest.value,
  })
  interest.value = []
}


</script>

<template>
  <form>
    <div class="form-control">
      <label for="user-name">Your Name</label>
      <input id="user-name" name="user-name" type="text" v-model.trim="userName" v-focus />
    </div>
    <div class="form-control">
      <h2>What are you interested in?</h2>
      <div>
        <input id="interest-react" name="interest" type="checkbox" value="react" v-model="interest" />
        <label for="interest-react">React.js</label>
      </div>
      <div>
        <input id="interest-vue" name="interest" type="checkbox" value="vue" v-model="interest" />
        <label for="interest-vue">Vue.js</label>
      </div>
      <div>
        <input
          id="interest-angular"
          name="interest"
          type="checkbox"
          value="angular"
          v-model="interest"
        />
        <label for="interest-angular">Angular.js</label>
      </div>
    </div>
    <div v-if="isLoading">Loading...</div>
    <div v-else>{{ data }}</div>
    <div>
      <button @click.prevent="onSubmit">Save Data</button>
    </div>
  </form>
</template>

<style scoped>
form {
  margin: 2rem auto;
  max-width: 40rem;
  border-radius: 12px;
  box-shadow: 0 2px 8px rgba(0, 0, 0, 0.26);
  padding: 2rem;
  background-color: #ffffff;
}

.form-control {
  margin: 0.5rem 0;
}

label {
  font-weight: bold;
}

h2 {
  font-size: 1rem;
  margin: 0.5rem 0;
}

input,
select {
  display: block;
  width: 100%;
  font: inherit;
  margin-top: 0.5rem;
}

select {
  width: auto;
}

input[type="checkbox"],
input[type="radio"] {
  display: inline-block;
  width: auto;
  margin-right: 1rem;
}

input[type="checkbox"] + label,
input[type="radio"] + label {
  font-weight: normal;
}

button {
  font: inherit;
  border: 1px solid #0076bb;
  background-color: #0076bb;
  color: white;
  cursor: pointer;
  padding: 0.75rem 2rem;
  border-radius: 30px;
}

button:hover,
button:active {
  border-color: #002350;
  background-color: #002350;
}
</style>