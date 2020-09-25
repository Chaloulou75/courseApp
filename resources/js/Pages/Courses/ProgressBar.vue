<template>
    <div>
        <div class="w-full bg-gray-200 rounded">
            <div class="text-center text-white duration-500 bg-green-500 rounded-l transition-width" :style="'width:' + percentage + '%'">{{ percentage }}%</div>
        </div>
    </div>
</template>

<script>
export default {
    props: ['watchedEpisodes', 'episodes'],
    data() {
        return {
            watchedEpisodesData: this.watchedEpisodes
        }
    },
    computed: {
        percentage() {
            let filteredEp = this.episodes.filter(courseEp => {
                return this.watchedEpisodesData.find(watchedEp => {
                    return watchedEp.id === courseEp.id;
                });
            });
            return Math.ceil(filteredEp.length / this.episodes.length * 100);
        }
    },
    mounted() {
        eventBus.$on('toggleProgress', data => this.watchedEpisodesData = data);
    }
}
</script>
