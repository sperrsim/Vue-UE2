<template>
  <div id="app">
    <h1>5BHIT</h1>
    <form @submit.prevent="addNewSubject">
      <label>Enter new subject:</label>
      <input v-model="newSubject"/>
      <button>Add Subject</button>
    </form>
    <hr>
    <ul>
      <li v-for="item, index in subjects" key="index">
        {{item.content}}
        <button @click='deleteSubject(index)'>Delete</button>
      </li>
    </ul>
  </div>
</template>

<script>
import { ref } from 'vue'

export default {
 setup()
 {
   const newSubject = ref('lask');
   const subjects = ref([]);

   function addNewSubject()
   {
     
     subjects.value.push(
       {content: newSubject.value,}
     );
     newSubject.value = '';
     console.log(subjects.value);
   }

   function deleteSubject(index)
   {
     subjects.value.splice(index, 1);
   }

   return {
     newSubject,
     addNewSubject,
     subjects,
     deleteSubject
   };
 }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  color: #2c3e50;
  margin-top: 60px;
}
h3 {
  margin-bottom: 20px;
}
hr {
  margin-top: 20px;
  margin-bottom: 20px;
}
</style>
