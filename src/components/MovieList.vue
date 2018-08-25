<template>
    <div id="movie-list">
        <div v-if="filteredMovies.length">
            <movie-item v-for="(movie, index) in filteredMovies" v-bind:key="filteredMovies[index]" 
            :movie="movie.movie" 
            :sessions="movie.sessions"
            :day="day" ></movie-item>
        </div>
        <div v-else-if="movies.length">
            No movies found
        </div>
        <div v-else>
            Loading...
        </div>
    </div>
</template>

<script>
import genres from '../util/genres';
import MovieItem from './MovieItem.vue';

export default {
    props: [ 'genre', 'time', 'movies', 'day' ],
    methods: {
        moviePassesGenreFilter: function(movie)
        {
            if (!this.genre.length) {
                return true;
                } else {
                    let movieGenres = movie.movie.Genre.split(", ");
                    let matched = true;
                    this.genre.forEach(genre => {
                        if (movieGenres.indexOf(genre) === -1) {
                            matched = false;
                        }
                    });
                    return matched;
                }
        }
    },
    computed: {
        filteredMovies: function() {
            return this.movies.filter(this.moviePassesGenreFilter);
        }
    },
    components: {
        MovieItem
    }
}
</script>
<style>

</style>
