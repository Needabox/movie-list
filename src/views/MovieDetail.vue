<template>
    <div class="movie-detail p-10">
        <div class="grid grid-cols-1 md:grid-cols-12">
            <div class="col-span-12 md:col-span-4">
                <img :src="movie.Poster" alt="movie poster">
            </div>
            <div class="col-span-12 md:col-span-8 text-white">
                <h1 class="text-2xl md:text-4xl font-bold">{{ movie.Title}}</h1>
                <p class="text-sm md:text-md">{{movie.Ratings[0].Value }} in {{ movie.Ratings[0].Source }} | {{ movie.Year}} | {{ movie.Genre}}</p>
                <h1 class="text-md md:text-lg mt-4">{{ movie.Plot }}</h1>
                <div class="mt-4">
                    <h1 class="text-lg md:text-2xl">Actors : {{ movie.Actors }}</h1>
                    <h1 class="text-lg md:text-2xl">Writer : {{ movie.Writer }}</h1>
                </div>
            </div>
        </div>
    </div>
</template>

<script>
import { ref, onBeforeMount } from 'vue';
import { useRoute } from 'vue-router';
import env from '@/env.js';

export default {
    setup(){
        const movie = ref({});
        const route = useRoute();

        onBeforeMount(() => {
            fetch(`http://www.omdbapi.com/?apikey=${env.apikey}&i=${route.params.id}&plot=full`)
            .then(response => response.json())
            .then(data => {
                console.log(data.Plot)
                movie.value = data;
            });
        });

        return {
            movie
        }
    }
}
</script>

<style>

</style>