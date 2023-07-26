<script setup lang="ts">
import Card from './Card.vue';
import RocketIcon from './RocketIcon.vue';
</script>

<template>
  <div class="container">
    <Card title="Title" class="card">
      <div class="contents">
        ここにさまざまなコンテンツが入ります
        <RocketIcon />
      </div>
    </Card>

    <Card title="Icons" class="card">
      <div class="contents">
        <RocketIcon />
        <RocketIcon />
        <RocketIcon />
        <RocketIcon />
      </div>
      <template #footer>
        <span>This is Footer</span>
        <RocketIcon size="20px" />
      </template>
    </Card>

    <Card title="Icons with Text" class="card with-text-card">
      <div class="contents">
        <RocketIcon />
        <span>Rocket</span>
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
