<script setup lang="ts">
const { data: joke } = await useFetch<any>("https://v2.jokeapi.dev/joke/Any");

const counter = useState("counter", () => 0);

function add() {
  counter.value++;
}

function subtract() {
  counter.value--;
}
</script>

<template>
  <div>
    <h1>Index page</h1>

    <div>Counter: {{ counter }}</div>

    <div>
      <button @click="add()">+</button>

      <button @click="subtract()">-</button>
    </div>

    <div>
      Category: {{ joke.category }}

      <p v-if="joke.type === 'single'">{{ joke.joke }}</p>

      <p v-else>{{ joke.setup }}<br />{{ joke.delivery }}</p>
    </div>

    <div>
      {{ JSON.stringify(joke) }}
    </div>
  </div>
</template>
