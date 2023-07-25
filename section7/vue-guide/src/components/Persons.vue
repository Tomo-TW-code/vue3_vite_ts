<template>
  <div class="container">
    <h1>Title</h1>
    <PersonPostForm @register="registerPerson"/>
    <div class="list-container">
      <ul>
        <PersonList :persons="persons" @delete="deletePerson"/>
      </ul>
    </div>
  </div>
</template>

<script setup lang="ts">
import { ref, Ref } from 'vue'
import PersonList from './PersonList.vue';
import PersonPostForm from './PersonPostForm.vue';

export type Person = {
  id: number,
  name: string,
  age: number,
}

const persons: Ref<Person[]> = ref([
  {id: 0, name: 'John', age: 24},
  {id: 1, name: 'Mike', age: 26}
])

const registerPerson = (person: Person) => {
  persons.value.push(person)
}

const deletePerson = (id: number) => {
  persons.value = persons.value.filter(p => p.id !== id)
}

</script>

<style scoped>

.container {
  display: flex;
  flex-direction: column;
  align-items: center;
}



</style>