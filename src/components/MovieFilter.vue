<template>
    <div id="movie-filter">
        <h2>Filter results</h2>
        <div class="filter-group">
            <check-filter v-for="(genre, index) in genres" :title="genre" v-bind:key="genres[index]" @check-filter="checkFilter"></check-filter>
        </div>
    </div>
</template>

<script>
import genres from '../util/genres';
import CheckFilter from './CheckFilter.vue';

export default {
    data: function() {
        return { 
            genres 
        };
    },
    methods: {
        checkFilter: function(category, title, checked) {
            this.$emit('check-filter', category, title, checked);
        }
    },
    components: {
        CheckFilter
    }
}
</script>
<style>

</style>
