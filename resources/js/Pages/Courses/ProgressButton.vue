<template>
    <div>
        <button class="px-4 py-1 text-white bg-green-500 rounded-lg hover:bg-green-600"
            @click="toggleProgress()">
            {{ this.isWatched ? 'Terminé' : 'Episode terminé?'}}
        </button>
    </div>

</template>
<script>
export default {
    props : ['episode-id', 'watchedEpisodes'],

    data(){
        return {
            watchedEp : this.watchedEpisodes,
            isWatched : null
        }
    },

    methods : {
        toggleProgress(){
            axios.post('/toggleProgress', {
                episodeId: this.episodeId,
            })
            .then(response => {
                if(response.status === 200){
                    this.isWatched = !this.isWatched;
                    eventBus.$emit('toggleProgress', response.data);
                }
            })
            .catch(error =>console.log(error));
        },
        isWatchedEpisode(){
            return this.watchedEp.find(episode => episode.id === this.episodeId) ? true : false;
        }
    },

    mounted(){
        this.isWatched = this.isWatchedEpisode();
    }
}
</script>
