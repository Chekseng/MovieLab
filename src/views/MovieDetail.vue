<template>
  <section class="movie-detail">
    <Navbar />

    <div class="movie-detail-body">
      <article class="detail-image">
        <img :src="movie.Poster" />
      </article>

      <article class="detail-info">
        <h2>{{movie.Title}}</h2>

        <p>{{movie.Plot}}</p>

        <table class="detail-table">

          <thead>
            <tr>
              <th>Detail</th>
              <th>Value</th>
            </tr>
          </thead>
          <tbody>
            <tr>
              <td>Genre: </td>     
              <td>{{movie.Genre}}</td>       
            </tr>

            <tr>
              <td>Rated: </td>
              <td>{{movie.Rated}}</td>
            </tr>
            <tr>
              <td>Cast: </td>
              <td>{{movie.Actors}}</td>
            </tr>
            <tr>
              <td>Country: </td>
              <td>{{movie.Country}}</td>
            </tr>
            <tr>
              <td>Released: </td>
              <td>{{movie.Released}}</td>
            </tr>
            <tr>
              <td>Runtime: </td>
              <td>{{movie.Runtime}}</td>
            </tr>
            <tr>
              <td>Type: </td>
              <td>{{movie.Type}}</td>
            </tr>
            <tr>
              <td>Year: </td>
              <td>{{movie.Year}}</td>
            </tr>
            <tr>
              <td>Votes: </td>
              <td>{{movie.imdbVotes}}</td>
            </tr>
            <tr>
              <td>Imdb Rating: </td>
              <td>{{movie.imdbRating}}</td>
            </tr>
            <tr>
              <td>Language: </td>
              <td>{{movie.Language}}</td>
            </tr>
          </tbody>
        </table>
      </article>
    </div>
  </section>

  <Footer />
</template>

<script>
import { ref, onBeforeMount } from 'vue'
import { useRoute } from 'vue-router'
import Navbar from '@/components/Navbar.vue'
import Footer from '@/components/Footer.vue'
export default {
  components: {
    Navbar,
    Footer
  },
  setup(){
    const movie = ref({})
    const route = useRoute();
    const VUE_APP_API_KEY = process.env.VUE_APP_API_KEY

    onBeforeMount(() => {
      fetch(`http://www.omdbapi.com/?apikey=${VUE_APP_API_KEY}&i=${route.params.id}&plot=full`)
        .then((response) => response.json())
        .then(data => {
          movie.value = data;
        })
    })

    return {
      movie
    }
  }
}
</script>

<style lang="scss">
  .movie-detail-body{
    display: grid;
    grid-template-columns: 35% 60%;
    width: 60%;
    margin: 0 auto;
    padding: 30px 0;
    align-items: start;
    grid-gap: 10px 20px;

    @media screen and (max-width: 1100px){
      width: 80%;
    }

    @media screen and (max-width: 900px){
      grid-template-columns: 100%;
      grid-gap:  40px 0;
    }

    .detail-image{

      background-color: var(--secondary-bg);
      display: grid;
      border-radius: 10px;
      
      img{
        object-fit: fill;
        width: 100%;
        border-radius: 10px;
        padding: 10px;
      }
    }

    .detail-info{
      h2{
        color: var(--primary-text-color);
        font-size: 30px;
        padding-bottom: 10px;
      }

      > p{
        color: var(--tetiary-text-color);
        font-size: 20px;
        padding-bottom: 30px;
      }

      .detail-table{
        thead{
          tr{
            display: flex;
            justify-content: space-between;
            color: var(--primary-text-color);
            font-size: 20px;

            th:first-child{
              padding-left: 10px;
            }
            th:last-child{
              padding-right: 20px;
            }
          }
        }

        tbody{
          tr{
            display: flex;
            flex-flow: row;
            width: 100%;
            justify-content: space-between;
            color: var(--secondary-text-color);
            border-bottom: 1px solid var(--secondary-text-color);
            padding: 10px;

            td:first-child{
              font-weight: bold;
              font-size: 17px;
            }
          }
        }
      }
    }
  }
</style>