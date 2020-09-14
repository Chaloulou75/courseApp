<template>
    <app-layout>
        <template slot="header">
            {{ course.title }}
        </template>
        <div class="container mx-8 my-4">
            <div class="py-4 text-3xl text-gray-600">{{ this.courseShow.episodes[this.currentKey].title }}</div>
            <iframe class="w-full h-screen" :src="this.courseShow.episodes[this.currentKey].video_url" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

            <div class="py-4 text-base text-gray-500">{{ this.courseShow.episodes[this.currentKey].description }}</div>

            <div class="mt-8">
                <ul v-for="(episode, index) in this.course.episodes" v-bind:key="episode.id">
                    <li class="mt-3">
                        Episode n° {{ index +1 }} - {{ episode.title }}
                        <button class="text-gray-500 focus:outline-none focus:text-gray-400"
                                @click="switchEpisode(index)">
                            Voir l'épisode
                        </button>
                    </li>
                </ul>
            </div>
        </div>
    </app-layout>
</template>

<script>
    import AppLayout from './../../Layouts/AppLayout'

    export default {
        components: {
            AppLayout
        },
        props : ['course'],

        data() {
            return {
                courseShow: this.course,
                currentKey : 0
            }
        },

        methods:{
            switchEpisode(index){
                this.currentKey = index;
                window.scrollTo({
                    top:0,
                    left:0,
                    behavior:'smooth'
                });
            }
        },


    }
</script>
