<script setup>
import { reactive } from 'vue';

const saarcCountries = reactive([
  { name: "Bangladesh", capital: "Dhaka" },
  { name: "Nepal", capital: "Kathmandu" },
  { name: "Bhutan", capital: "Thimphu" },
  { name: "Sri Lanka", capital: "Colombo" },
  { name: "India", capital: "New Delhi" },
  { name: "Pakistan", capital: "Islamabad" },
  { name: "Maldives", capital: "Male" }
])

const capitals = ["Dhaka", "Kathmandu", "Thimphu", "Colombo", "New Delhi", "Islamabad", "Male"]

const getScore = () => {
  let score = 0
  saarcCountries.forEach(country => {
    if(country.capital === country.answer){
      score++
    }
  })
  return score;
}

</script>

<template>
   <section class="mx-auto container text-left">
    <h1 class="text-2xl mb-10">Vue Form</h1>
    <p class="mb-10"> {{ saarcCountries }} </p>
    <p>Your Score: {{ getScore() }} </p>
    <div class="my-5 border border-gray-400 p-5" v-for="(country, index) in saarcCountries" :key="index">
      <p>What is the capital of {{ country.name }}? </p>
      <templat v-for="(capital, index) in capitals" :key="index">
        <input type="radio" :value="capital" :name="country.name" v-model="country.answer"/> 
        <label class="ml-2 mr-2"> {{ capital }} </label>
      </templat>
    </div>
  </section>
</template>

<style scoped>

</style>
