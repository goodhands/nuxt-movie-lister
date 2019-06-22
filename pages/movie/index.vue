<template>
  <div>
    <navbar />
    <Header />
    <section class="section">
      <div class="container">
        <div class="columns is-multiline">
          <div class="column is-3" v-for="(movie, index) in movies" :key="index">
            <div class="card">
              <div class="card-image">
                <figure class="image is-4by3">
                  <img :src="movie.Poster" :alt="movie.Title">
                </figure>
              </div>
              <div class="card-content">
                <div class="content">
                  <h2 class="title">
                    <NuxtLink :to="{ name: 'movie-id', params: {id: movie.imdbID} }">
                      {{movie.Title}}
                    </NuxtLink>
                  </h2>
                  <br>
                  <p class="subtitle">{{movie.Plot}}</p>
                  <time datetime="2016-1-1">Released in {{movie.Year}}</time>
                </div>
              </div>
          </div>
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

    asyncData({ req, params }) {
        // We can return a Promise instead of calling the callback
        return axios.get('http://www.omdbapi.com/?s=love&apikey=713602fe&plot=full&y=2018')
        .then((res) => {
            return { movies: res.data.Search }
        })
    },

    head: {
        title: 'Best movie listing site!'
    }

}
</script>