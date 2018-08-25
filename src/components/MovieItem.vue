<template>
    <div class="movie">
        <div class="movie-col-left">
            <img :src="movie.Poster" alt="">
        </div>
        <div class="movie-col-right">
            <div class="movie-title">
                <h2>{{movie.Title}}</h2>
                <span class="movie-rating">{{movie.Rated}}</span>
            </div>
            <div class="movie-sessions">
                <div v-for="(session, index) in filteredSessions(sessions)" :key="index" class="session-time-wrapper">
                    <div class="session-time">{{ formatSessionTime(session.time)}}</div>
                </div>
            </div>
        </div>
    </div>
</template>
<script>
export default {
    props: ['movie', 'sessions', 'day'],
    methods: {
        formatSessionTime(raw) {
            return this.$moment(raw).format('h:mm A');
        },
        filteredSessions: function(sessions){
            var vm = this;
            return sessions.filter(function(session) {
                return vm.$moment(session.time).isSame(vm.day, 'day');
            });
        }
    }
}
</script>
<style>

</style>
