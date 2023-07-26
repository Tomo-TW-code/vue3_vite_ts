<script setup lang="ts">
import { ref, computed } from 'vue'
import CardList from './components/CardList.vue';
import SecondCardList from './components/SecondCardList.vue';

// const isFirstTab = ref(true)
const isActiveTabName = ref('1')
const updateTab = (activeName: string) => {
  isActiveTabName.value = activeName
}

const currentComponent = computed(() => {
  switch (isActiveTabName.value) {
    case '1':
      return CardList
    case '2':
      return SecondCardList
    case '3':
      return CardList
    default:
      return CardList
  }
})

</script>

<template>
  <div class="tab-changer">
    <button @click="updateTab('1')">Tab 1</button>
    <button @click="updateTab('2')">Tab 2</button>
    <button @click="updateTab('3')">Tab 3</button>
  </div>
  <div class="tab-contents">
    <component :is="currentComponent"></component>
  </div>
</template>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}

.tab-contents {
  margin-top: 20px;

}
</style>
