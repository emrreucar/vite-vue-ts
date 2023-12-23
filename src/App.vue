<template>
  <div class="app">
    <header>
      <div class="title">
        <img src="./assets/heart.svg" alt="site logo" />
        <h1>Hyrule Jobs</h1>
      </div>
      <div class="order">
        <button @click="handleClick('title')">order by title</button>
        <button @click="handleClick('salary')">order by salary</button>
        <button @click="handleClick('location')">order by location</button>
      </div>
    </header>
    <JobList :jobs="jobs" :order="order" />
  </div>
</template>

<script setup lang="ts">
import JobList from "./components/JobList.vue";
import { Job } from "./types/Job";
import OrderTerm from "./types/OrderTerm";

import { ref } from "vue";

const jobs = ref<Job[]>([
  { title: "farm worker", location: "lon lon ranch", salary: 30000, id: 1 },
  { title: "quarryman", location: "death mountain", salary: 40000, id: 2 },
  { title: "flute player", location: "the lost woods", salary: 35000, id: 3 },
  { title: "fisherman", location: "lake hylia", salary: 21000, id: 4 },
  { title: "prison guard", location: "gerudo valley", salary: 32000, id: 5 },
]);

const order = ref<OrderTerm>("title");

const handleClick = (term: OrderTerm) => {
  order.value = term;
};
</script>

<style>
header {
  text-align: center;
}
header .order {
  margin-top: 20px;
}
header .title {
  display: flex;
  justify-content: center;
}
header img {
  width: 60px;
  margin-right: 20px;
}
button {
  margin: 0 10px;
  color: #0000009c;
  border: 2px solid #1195c9;
  background: #d6d5ffa8;
  padding: 8px 16px;
  border-radius: 4px;
  cursor: pointer;
  font-weight: bold;
  text-transform: uppercase;
}

button:hover {
  background-color: #1195c9;
  color: white;
  transition: 0.4s;
}
</style>
