<template>
  <div class="form-container">
    <input v-model="inputtingDescription"/>
    <button class="save-button" @click="postTweet">post</button>
  </div>
</template>

<script setup lang="ts">
import { ref } from 'vue'
const inputtingDescription = ref<string>('')

const postTweet = () => {
}

</script>

<style scoped>
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

button:hover {
  filter: brightness(85%) contrast(130%);
}


</style>