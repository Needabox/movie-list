<template>
  <div class="home">
    <router-link to="/movie/tt4906830">
      <div class="sliderAx h-auto">
        <div id="slider-1" class="container mx-auto">
          <div class="bg-cover bg-center  h-auto text-white py-24 px-10 object-fill" style="background-image: url(https://i.pinimg.com/originals/ca/2d/9a/ca2d9a862d2948dc7815f68529d84d12.png)">
            <div class="md:w-1/2">
              <p class="text-2xl md:text-3xl font-bold">MoviesList</p>
              <p class="text-xl md:text-2xl mb-10 leading-none">Find the movie you like here</p>
            </div>  
          </div>
          <br>
        </div>
      </div>
    </router-link>
    <form @submit.prevent="SearchMovies()" action="">
      <div class="grid grid-cols-1 md:grid-cols-12 px-5 md:px-10">
        <div class="col-span-11 px-0 md:px-10">
        <input class="w-full h-10 md:h-12 rounded mb-4 focus:outline-none focus:shadow-outline text-md md:text-xl px-4 shadow-lg" type="search" placeholder="Search movie you want..." v-model="search">
        </div>
        <div class="col-span-1 justify-item-center items-center">
          <button class="bg-green-500 hover:bg-green-700 text-white font-bold py-2 md:py-3 px-4 md:px-8 rounded" type="submit" value="search">
          Search
        </button>
        </div>
      </div>
    </form>

    <div class="movies-list mt-4">
      <div class="grid grid-cols-1 md:grid-cols-3 justify-items-center p-4 md:p-0">
        <div v-for="movie in movies" :key="movie.imdbID" class="mb-4">
          <div class="col-span-12">
            <router-link :to="'/movie/' + movie.imdbID">
              <div class="max-w-sm rounded bg-white">
                <img class="w-full rounded-t" :src="movie.Poster">
                  <div class="px-6 py-4">
                    <div class="font-bold text-xl tracking-wide">{{ movie.Title }}</div>
                    <div class="text-gray-500 text-sm mb-3">{{ movie.Year }}</div>
                  </div>
              </div>
            </router-link>
          </div>
        </div>
      </div>
    </div>

    
  </div>
</template>

<script>
import { ref } from 'vue';
import env from '@/env.js'

export default {
  setup() {
    const search = ref("");
    const movies = ref([]);

    const SearchMovies = () => {
      if (search.value != "") {
        fetch(`https://www.omdbapi.com/?apikey=${env.apikey}&s=${search.value}`)
        .then(response => response.json())
        .then(data => {
          movies.value = data.Search;
          search.value = "";
        });
      }
    }
    return {
      search,
      movies,
      SearchMovies
    }
  }
}
</script>
