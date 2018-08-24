<template>
    <div id="movie-list">
        <div v-for="(movie, index) in filteredMovies" v-bind:key="filteredMovies[index]" class="movie">
            {{ movie.title }}
        </div>
    </div>
</template>

<script>
import genres from '../util/genres';

export default {
    data: function() {
        return {
            movies: [
            { title: 'Pulp Fiction', genre: genres.HORROR },
            { title: 'Home Alone', genre: genres.COMEDY },
            { title: 'Austin Powers 2', genre: genres.COMEDY }
            ]
        }
    },
    props: [ 'genre', 'time' ],
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
    }
}
</script>
<style>

</style>
