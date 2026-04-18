<script setup>
import { reactive } from 'vue';
const movies = reactive ([
   { id: 1, title: 'The Shawshank Redemption', year: 1994 },
   { id: 2, title: 'The Godfather', year: 1972 },
   { id: 3, title: 'The Dark Knight', year: 2008 }
]);

const newMovie = reactive({
   title: '',
   year: null
});

const addMovie = () => {
   // Logic to add a movie
   movies.push({id: movies.length +1 , title: newMovie.title, year: newMovie.year});
   newMovie.title = '';
   newMovie.year = null;
};

const removeMovie = () =>{
   // Logic to remove a movie
   movies.pop();
}
</script>

<template>
   <div class="app">
      <h1>Basic Form</h1>
       <form>
         <div class="input-group">
            <label for="title">Title:</label>
            <input type="text" id="title" name="title" v-model="newMovie.title" />
         </div>
         <div class="input-group">
            <label for="year">Year:</label>
            <input type="number" id="year" name="year" v-model="newMovie.year" />
         </div>
         <div class="button-group">
            <button type="button" @click="addMovie">Add</button>
            <button type="button" @click="removeMovie">Remove</button>
         </div>

         <div class="movie-group">
            <h2>Movies</h2>
            <ul>
               <li v-for="movie in movies" :key="movie.id">
                  <span>{{ movie.title }} ({{ movie.year }})</span>
               </li>
            </ul>
         </div>
      </form>
   </div>
</template>

<style scoped>

</style>
