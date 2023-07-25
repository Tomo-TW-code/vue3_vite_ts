<template>
  <!-- v-for -->
  <li v-for="tweet in tweets" :key="tweet.id" class="tweet-list">
    <span>{{ tweet.description }}</span>
    <button @click="deleteTweet(tweet.id)" class="delete-button">delete</button>
  </li>
</template>

<script setup lang="ts">
  import { defineProps, defineEmits } from 'vue';

  /* 型エイリアス： TypeScript独特の構文でオブジェクトや配列の型を強制するもの */
  type Tweet = {
    id: number,
    description: string,
  }

  type Props = {
    tweets: Tweet[]
    // deleteTweet: (id: number) => void
  }

  // PropsはdefinePropsで定義すると親から子へ値を渡すことができる
  defineProps<Props>()

  const emit = defineEmits(['delete-tweet'])
  const deleteTweet = (id: number) => {
    emit('delete-tweet', id)
  }

</script>

<style scoped>
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