<script setup lang="ts">
import { ref } from 'vue'

// tweets:ref関数でリアクティブ化した変数
const tweets = ref([
  {id: 0, description: 'Hello, World!'},
  {id: 1, description: 'This is the second tweeet.'}
])
// v-modelでtweet情報を結びつける変数
const inputtingDescription = ref<string>('')

// postボタンの処理
const postTweet = () => {
  const tweet = {
    id: Math.random(),
    description: inputtingDescription.value
  }
  tweets.value.push(tweet)
  console.log('post...', tweets.value)
}

// deleteボタンの処理
// リアクティブな値から、動的に値を削除するための処理
const deleteTweet = (id: number) => {
  // 押されたid以外のtweetsを返す（実質のデリート処理）
  tweets.value = tweets.value.filter(t => t.id !== id)
}

</script>

<template>
  <div class="container">
    <h1>Tweeter</h1>
    <div class="form-container">
      <input v-model="inputtingDescription"/>
      <button class="save-button" @click="postTweet()">post</button>
    </div>
    <div class="tweet-container">
      <!-- v-if, v-show:
        v-ifの方が切り替えのコストが高いので、
        上記2つを使い分けるが基本的にはv-ifでOK
      -->
      <p v-if="tweets.length <= 0">No tweets have been added</p>
      <ul v-else>
        <!-- v-for -->
        <li v-for="tweet in tweets" :key="tweet.id" class="tweet-list">
          <span>{{ tweet.description }}</span>
          <button @click="deleteTweet(tweet.id)" class="delete-button">delete</button>
        </li>
      </ul>
    </div>
  </div>
</template>

<style scoped>
.container {
  display: flex;
  flex-direction: column;
  align-items: center;
}

.form-container {
  display: flex;
  flex-direction: column;
  align-items: center;
  row-gap: 20px;
  background-color: aliceblue;
  padding: 24px 0;
  width: 60%;
  margin-bottom: 12px;
  border-radius: 4px;
}

.tweet-list {
  list-style: none;
  display: flex;
  justify-content: space-between;
  background-color: rgb(204, 219, 233);
  width: 300px;
  padding: 8px 20px;
  margin-bottom: 12px;
  border-radius: 4px;
  font-size: 12px;
}

.save-button {
  color: #fff;
  font-weight: bold;
  background-color: #68c9c9;
  border: none;
  border-radius: 2px;
  width: 60px;
  height: 22px;
  cursor: pointer;
  transition: filter .25s;
}

.delete-button {
  color: #fff;
  font-weight: bold;
  background-color: #c99a68;
  border: none;
  border-radius: 2px;
  width: 60px;
  height: 22px;
  cursor: pointer;
  transition: filter .25s;
}

button:hover {
  filter: brightness(85%) contrast(130%);
}

</style>