<template>
  <div class="form-container">
    <div class="input-container">
      <div class="input-column">
        <span>name:</span>
        <input class="input-name" v-model="inputtingName" />
      </div>
      <span class="error-message" v-if="!isValidName">{{ nameLengthLimit }} characters ore less, please</span>
      <div class="input-column">
        <span>age:</span>
        <input type="number" class="input" v-model="inputtingAge" />
      </div>
    </div>
    <button :disabled="!isValidName" @click="register" class="register-button">register</button>
  </div>
</template>

<script setup lang="ts">
import { ref, computed } from 'vue'

const inputtingName = ref<string>('')
const inputtingAge = ref<number>(0)

const emit = defineEmits(['register'])

const register = () => {
  const person = {
    id: Math.random(),
    name: inputtingName.value,
    age: inputtingAge.value
  }
  console.log('person ..', person)
  emit('register', person)
}

// 名前のバリデーション処理
const nameLengthLimit = 15
const isValidName = computed(() => {
  if (inputtingName.value.length >= nameLengthLimit) {
    return false
  } else {
    return true
  }
})

const validationColor = computed(() => {
  return isValidName.value ? 'white' : 'rgb(244,194,190)'
})

</script>

<style scoped>
.form-container {
  display: flex;
  flex-direction: column;
  align-items: center;
  background-color: rgb(255, 241, 226);
  width: 50%;
  margin-bottom: 12px;
  border-radius: 4px;
  padding: 24px 0;
}

.input-container {
  display: flex;
  flex-direction: column;
  justify-content: space-between;
  height: 50px;
  margin-bottom: 20px;
}

.input-column {
  width: 200px;
  display: flex;
  justify-content: space-between;
}

.input-name {
  background-color: v-bind(validationColor);
}


input {
  width: 120px;
  margin-bottom: 8px;
}

span {
  font-size: 20px;
  font-weight: bold;
}

.error-message {
  font-size: 12px;
  color: rgb(244, 194, 190);
}

</style>