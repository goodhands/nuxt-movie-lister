<template>
  <div>
    <navbar />
    <Header />
    <section class="section">
      <div class="container">
          <h2 class="title">{{movies.Title}}</h2>
          <p class="subtitle">
              {{movies.Plot}}
          </p>
          <div class="columns">
              <div class="column is-4">
                <figure class="image is-2by3">
                    <img :src="movies.Poster">
                </figure>
              </div>
              <div class="column is-8">
                  <h4 class="title is-5">Movie details</h4>
                  <b>Genre:</b> {{movies.Genre}} <br>
                  <b>Language:</b> {{movies.Language}} <br>
                  <b>Country:</b> {{movies.Country}} <br>
                  <b>Awards:</b> {{movies.Awards}} <br>
                  <b>Runtime:</b> {{movies.Runtime}} <br>
                  <b>Released:</b> {{movies.Released}} <br>
                  <b>Rated:</b> {{movies.Rated}} <br>
                  <b>Writer:</b> {{movies.Writer}} <br>
              </div>
          </div>

      </div>
    </section>

  </div>
</template>

<script>
import Logo from '~/components/Logo.vue'
import Navbar from '~/components/Navbar.vue'
import Header from '~/components/Header.vue'
import axios from 'axios'

export default {
  components: {
    Logo,
    Navbar,
    Header
  },

    async asyncData({ params }) {
        // We can return a Promise instead of calling the callback
        const { data } = await axios.get(`http://www.omdbapi.com/?i=${params.id}&apikey=713602fe`);
        return { movies: data }
    },

    head() {
        return{
        //    title: this.movies.Title
        }
    }

}
</script>