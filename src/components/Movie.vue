<script setup>
import { ref } from "vue";
import axios from "axios";
 
const id = ref("");
const movie = ref(null);
 
const getMovies = async () => {
  const data = id.value;
  movie.value = (
    await axios.get(`https://api.themoviedb.org/3/movie/${data}`, {
      params: {
        api_key: "57d676ce947993ee4ca284e602601ec8",
        append_to_response: "videos",
      },
    })
  ).data;
};
</script>
 
<template>
  <select v-model="id">
    <option value="315635">Spider-Man: Homecoming</option>
    <option value="283995">Guardians of the Galaxy Vol. 2</option>
    <option value="10191">How to Train Your Dragon</option>    
    <option value="1726">Iron Man</option>
    <option value="10195">Thor</option>
    <option value="9615">The Fast and the Furious: Tokyo Drift</option>
    <option value="324552">John Wick: Chapter 2</option>  
    <option value="20453">3 Idiots</option>  
    <option value="272">Batman Begins</option>  
    <option value="9502">Kung Fu Panda</option>  
  </select>
  <button @click="getMovies">Get</button>
  <div v-if="movie" class="movie-container">
    <h1>{{movie.original_title}}</h1>
    <h1>Release Date: {{movie.release_date}}</h1>
    <img :src="`https://image.tmdb.org/t/p/w500/${movie.poster_path}`">
    <h1>Adult: {{movie.adult}}</h1>
    <h1>Movie Popularity: {{movie.popularity}}</h1>
    <h1>Language: {{movie.original_language}}</h1>
    <h1>Vote Count: {{movie.vote_count}}</h1>
    <h1>Vote Avarage: {{movie.vote_avarage}}</h1>
    <h1>Overview: {{movie.overview}}</h1>
    <iframe :src="`https://www.youtube.com/embed/${movie.videos.results.filter((video) => video.type === 'Trailer').at(0).key}`"></iframe>
    
 
  </div>
</template>
 
<style scoped>
iframe{
  height: 444px;
  width: 790px;
}
h1{
  color: white;
  font-family: monospace;
}

select{
  color: white;
  background-color: black;
  font-family: monospace;
  height: 50px;
  width: 350px;
  
}
button{
  color: white;
  background-color: black;
  border-color: white;
  font-family: monospace;
  height: 50px;
  width: 70px;
}
</style>