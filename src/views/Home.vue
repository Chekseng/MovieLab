<template>
  <section class="container">
    
    <article class="banner">
      <h1>Movie <span>Lab</span></h1>
    </article>

    <article class="search-bar">
      <form @submit.prevent="searchMovies()">
        <input type="text" placeholder="Search Movie" v-model="search" />
      </form>
    </article>

    <article class="movie-info">
      
      <div v-for="movie in movies" :key="movie.imdbID" class="movie-container">
        
        <router-link :to="'/movie/' + movie.imdbID" class="movie-link">
          
          <img :src="movie.Poster" alt="movie poster"  />
        </router-link>
      </div>

    </article>
  </section>
</template>

<script>
// @ is an alias to /src
import { ref } from 'vue';
import env from '@/env.js'

export default {
  name: 'Home',
  components: {
  },
  setup(){
    const search = ref('')
    const movies = ref([])
    const searchMovies = () => {
      if(search.value != ''){
        fetch(`http://www.omdbapi.com/?apikey=${env.apiKey}&s=${search.value}`)
          .then((response) => response.json())
          .then(data => {
            movies.value = data.Search;
            search.value = '';
            console.log(movies.value)
          })
      }
    }

    return{
      search,
      movies,
      searchMovies,
    }
  }
}
</script>

<style lang="scss">
.container{
  .banner{
    background-image: linear-gradient(rgba(0,0,0,0.5), rgba(0,0,0,0.9)),url('../assets/banner-background.jpg');
    padding: 170px 0;

      h1{
        @media screen and (max-width: 500px){
          font-size: 40px;
        }
        color: var(--primary-text-color);
        font-weight: 800;
        font-size: 60px;
        text-align: center;
        color: var(--tetiary-text-color);
        text-transform: uppercase;

        span{
          color: var(--primary-text-color);
        }
      }    
  }

  .search-bar{
    @media screen and (max-width: 1000px){
      width: 60%;
    }

    @media screen and (max-width: 500px){
      width: 70%;
      // margin-right: 50px;
    }
    width: 40%;
    padding: 40px 0;
    margin: 0 auto;
     
    input{
      width: 100%;
      padding: 20px;
      font-size: 20px;
      border: none;
      background-color: rgb(68, 88, 167);
      border-radius: 10px;
      color: var(--quatenary-text-color);
    }

    input::placeholder{
        color: var(--tetiary-text-color);
        font-weight: lighter;
        font-style: italic;
      }
  }

  .movie-info{

    @media screen and (max-width:1400px){
      width: 80%;
    }

    @media screen and (max-width: 1200px){
      width: 90%;
    }

    @media screen and (max-width: 1100px){
      grid-template-columns: 28% 28% 28%;
      grid-gap: 20px 60px;
    }

    @media screen and (max-width: 1000px){
      grid-template-columns: 50% 50%;
      justify-content: center;
      grid-gap: 20px 50px;
      width: 70%;
    }

    @media screen and (max-width: 800px){
      width: 70%;
      grid-template-columns: 100%;
      grid-gap: 20px 0;
    }

    display: grid;
    grid-template-columns: 32% 32% 32%;
    width: 70%; 
    margin: 0 auto;
    justify-content: center;
    align-items: stretch;
    grid-gap: 20px 0;

    .movie-link{
      :hover{
        opacity: 0.5;
      }

      img{
        object-fit: cover;
        border-radius: 10px;
      }
    }
  }
}
</style>
