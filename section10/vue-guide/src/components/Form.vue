<script setup lang="ts">
import { DirectiveBinding, ref } from 'vue'

const userName = ref<string>('')
// 自作ディレクティブ v-focus
const vFocus = {
  mounted: (el: HTMLElement, binding: DirectiveBinding) => {
    el.focus()

    if (binding.modifiers.alert) {
      el.style.backgroundColor = 'pink'
    }
  }
}

const onSubmit = () => {
  // e.preventDefault()
  console.log('userName ', userName)
  console.log('submit')
}

</script>

<template>
  <form>
    <div class="form-control">
      <label for="user-name" v>Your Name</label>
      <input v-model.trim="userName" id="user-name" name="user-name" type="text" v-focus.alert />
    </div>
    <div class="form-control">
      <label for="age">Your Age</label>
      <input id="age" name="age" type="number" />
    </div>
    <div class="form-control">
      <label for="from">Where Are you from?</label>
      <select id="from" name="from">
        <option value="japan">Japan</option>
        <option value="china">China</option>
        <option value="others">Others</option>
      </select>
    </div>
    <div class="form-control">
      <h2>What are you interested in?</h2>
      <div>
        <input id="interest-react" name="interest" type="checkbox" />
        <label for="interest-react">React.js</label>
      </div>
      <div>
        <input id="interest-vue" name="interest" type="checkbox" />
        <label for="interest-vue">Vue.js</label>
      </div>
      <div>
        <input id="interest-angular" name="interest" type="checkbox" />
        <label for="interest-angular">Angular.js</label>
      </div>
    </div>
    <div class="form-control">
      <h2>How do you learn?</h2>
      <div>
        <input id="how-video" name="how" type="radio" />
        <label for="how-video">Video Courses</label>
      </div>
      <div>
        <input id="how-books" name="how" type="radio" />
        <label for="how-books">Books</label>
      </div>
      <div>
        <input id="how-other" name="how" type="radio" />
        <label for="how-other">Other</label>
      </div>
    </div>
    <div>
      <!-- ディレクティブに繋がったmodifiers（修飾子） -->
      <button @click.prevent="onSubmit">Save Data</button>
    </div>
  </form>
</template>

<style scoped>
form {
  margin: 2rem auto;
  max-width: 40rem;
  border-radius: 12px;
  box-shadow: 0 2px 8px rgba(0, 0, 0, 0.26);
  padding: 2rem;
  background-color: #ffffff;
}

.form-control {
  margin: 0.5rem 0;
}

label {
  font-weight: bold;
}

h2 {
  font-size: 1rem;
  margin: 0.5rem 0;
}

input,
select {
  display: block;
  width: 100%;
  font: inherit;
  margin-top: 0.5rem;
}

select {
  width: auto;
}

input[type="checkbox"],
input[type="radio"] {
  display: inline-block;
  width: auto;
  margin-right: 1rem;
}

input[type="checkbox"] + label,
input[type="radio"] + label {
  font-weight: normal;
}

button {
  font: inherit;
  border: 1px solid #0076bb;
  background-color: #0076bb;
  color: white;
  cursor: pointer;
  padding: 0.75rem 2rem;
  border-radius: 30px;
}

button:hover,
button:active {
  border-color: #002350;
  background-color: #002350;
}
</style>