<template>
    <app-layout>
        <template slot="header">
            Liste des formations
        </template>
        <div v-for="course in courseList" v-bind:key="course.id" class="mx-8 my-4">
            <div class="px-4 py-2 text-gray-700 bg-green-300 border rounded">
                <div class="text-base text-cool-gray-600">Mise en ligne par {{ course.user.name }}</div>
                <div class="flex items-center justify-between">
                    <div class="text-2xl font-semibold ">{{ course.title }}</div>
                    <div class="text-sm text-gray-600 underline">{{ course.episodes_count }} episodes</div>
                </div>

                <div class="text-sm text-gray-600">{{ course.description }}</div>
                <a :href="'course/' + course.id" class="inline-block px-3 py-1 mt-3 text-sm text-white bg-gray-600 rounded-lg hover:bg-gray-700">Voir la formation</a>
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
        data() {
            return {
              courseList: this.courses
            }
        },
        props : ['courses']
    }
</script>
