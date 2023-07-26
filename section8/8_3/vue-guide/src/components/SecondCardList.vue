<script setup lang="ts">
import Card from './Card.vue';
import RocketIcon from './RocketIcon.vue';
</script>

<template>
  <div class="container">
    <Card title="Title" class="card">
      <div class="contents">
        2つ目のタブです
        <RocketIcon />
      </div>
    </Card>
  </div>
</template>

<style>
.container {
  display: flex;
  flex-direction: column;
  align-items: center;
}

.card {
  margin-bottom: 24px;
}

.card .contents {
  margin-top: 8px;
  display: flex;
}

.with-text-card span {
  font-size: 26px;
}
</style>
