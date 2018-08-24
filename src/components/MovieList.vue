<template>
    <div id="movie-list">
        <movie-item v-for="(movie, index) in filteredMovies" v-bind:key="filteredMovies[index]" :movie="movie" class="movie">
        </movie-item>
    </div>
</template>

<script>
import genres from '../util/genres';
import MovieItem from './MovieItem.vue';

export default {
    props: [ 'genre', 'time', 'movies' ],
    methods: {
        moviePassesGenreFilter: function(movie)
        {
            if (!this.genre.length) {
                return true;
                } else {
                return this.genre.find(
                    function(genre) {
                        return movie.genre === genre;
                    }
                )
                    // genre => movie.genre === genre);
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
