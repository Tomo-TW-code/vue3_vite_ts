<template>
  <div class="container">
    <h1>Tweeter</h1>
    <TweetPostForm @post-tweet="postTweet" />
    <div class="tweet-container">
      <!-- v-if, v-show:
        v-ifの方が切り替えのコストが高いので、
        上記2つを使い分けるが基本的にはv-ifでOK
      -->
      <p v-if="tweets.length <= 0">No tweets have been added</p>
      <ul v-else>
        <!-- propsで親から子へtweetsを渡す -->
        <TweetList :tweets="tweets" @delete-tweet="deleteTweet" />
      </ul>
    </div>
  </div>
</template>

<script setup lang="ts">
import TweetList from './TweetList.vue'
import TweetPostForm from './TweetPostForm.vue'
import { ref } from 'vue'

// tweets:ref関数でリアクティブ化した変数
const tweets = ref([
  {id: 0, description: 'Hello, World!'},
  {id: 1, description: 'This is the second tweeet.'}
])

// postボタンの処理
const postTweet = (description: string) => {
  const tweet = {id: Math.random(), description}
  tweets.value.push(tweet)
}

// deleteボタンの処理
// リアクティブな値から、動的に値を削除するための処理
const deleteTweet = (id: number) => {
  // 押されたid以外のtweetsを返す（実質のデリート処理）
  tweets.value = tweets.value.filter(t => t.id !== id)
}

</script>

<style scoped>
.container {
  display: flex;
  flex-direction: column;
  align-items: center;
}

</style>