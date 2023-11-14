<script setup>
import { ref } from 'vue'

const title = ref('Subh naam : A lucky name selector')
const nameChoice = ref('')
const nameChoiceList = ref([])
let nameSelected = ref('')
let showLuckyName = ref(false)

const addNameToNameChoiceList = () => {
  nameChoiceList.value.push(nameChoice.value)
  nameChoice.value = ''
}

const selectTheLuckyName = () => {
  if (nameChoiceList.value.length > 1) {
    const randomIndex = Math.floor(Math.random() * nameChoiceList.value.length)
    nameSelected.value = nameChoiceList.value[randomIndex]
    console.log(randomIndex)
    showLuckyName.value = true
  }
}
</script>

<template>
  <div class="shub-naam">
    <h1 class="shub-naam__title">{{  title  }}</h1>
    <div class="shub-naam-form">
      <div class="shub-naam-form-group">
        <label for="addName">Enter you name choice here</label>
        <input type="text" id="addName" v-model="nameChoice">
      </div>
      <div class="shub-naam-form-group">
        <button @click="addNameToNameChoiceList()">Add Name Choice</button>
      </div>
    </div>
    <div class="shubh-naam__list">
      <ul>
        <li v-for="(nameChoice) in nameChoiceList">
           {{  nameChoice }}
        </li>
      </ul>
    </div>
    <div class="shubh-naam__button" v-if="nameChoiceList.length > 1">
      <button @click="selectTheLuckyName()">Select the lucky name</button>
    </div>
    <p v-if="showLuckyName">Congratulation! the lucky name for your newborn is {{  nameSelected }}</p>
  </div>
</template>

<style scoped>
  .shub-naam-form {
    display: flex;
    flex-direction: row;
    align-items: center;
    justify-content: center;
  }

  .shub-naam-form-group, label {
    margin: 4px;
  }

  .shubh-naam__list ul {
    list-style-type: none;
  }
</style>
