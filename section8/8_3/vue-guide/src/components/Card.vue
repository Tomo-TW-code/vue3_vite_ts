<script setup lang="ts">
import { defineProps } from 'vue'
defineProps<{
  title: string,
}>();
</script>

<template>
  <div class="card-container">
    <div class="content">
      <span class="title">{{ title }}</span>
      <slot></slot>
    </div>
    <div class="footer">
      <slot name="footer">
        <span>Default Footer</span>
      </slot>
    </div>
  </div>
</template>

<style scoped>
.card-container {
  box-shadow: 2, 8px, black;
  border-radius: 8px;
  padding: 20px 0px 0px 0px;
  width: 300px;
  background-color: #ccc;
  display: flex;
  flex-direction: column;
  align-items: center;
}

.content {
  padding: 0px 20px 0px 20px;
}

.title {
  font-size: 20px;
  font-weight: 600;
}

.footer {
  display: flex;
  height: 30px;
  background-color: rgb(22, 119, 203);
  width: 100%;
  border-radius: 0px 0px 8px 8px;
  justify-content: center;
  align-items: center;
}
</style>