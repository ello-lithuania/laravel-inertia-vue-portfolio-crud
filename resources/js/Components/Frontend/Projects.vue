<script setup>
import Project from './Project.vue';
import { ref } from 'vue';

const props = defineProps({
    skills: {
        type: Object
    },
    projects: {
        type: Object
    }
})

const filteredProjects = ref(props.projects.data)
const selectedSkill = ref('all')

const filterProjects = (id) => {
    console.log(id)
    if(id==='all') {
        filteredProjects.value = props.projects.data
        selectedSkill.value = id
    } else {
        filteredProjects.value = props.projects.data.filter(project => {
            return project.skill.id == id
        })
        selectedSkill.value = id
    }
}
</script>

<template>
    <div class="container mx-auto">

        <div class="text-sm font-medium text-center mb-12 text-gray-500 border-b border-gray-200 dark:text-gray-400 dark:border-gray-700">
            <ul class="flex flex-wrap items-center justify-center -mb-px">
                <li class="me-2">
                    <button @click="filterProjects('all')" :class="[selectedSkill === 'all' && 'font-bold text-white']" class="inline-block p-4 border-b-2 border-transparent rounded-t-lg hover:text-gray-600 hover:border-gray-300 dark:hover:text-gray-300">All</button>
                </li>
                <li class="me-2" v-for="project_skill in skills.data" :key="project_skill.id">
                    <button @click="filterProjects(project_skill.id)" :class="[selectedSkill === project_skill.id && 'font-bold text-white']" class="inline-block p-4 border-b-2 border-transparent rounded-t-lg hover:text-gray-600 hover:border-gray-300 dark:hover:text-gray-300">{{ project_skill.name }}</button>
                </li>
            </ul>
        </div>

        <section class="grid gap-y-12 lg:grid-cols-3 lg:gap-8">
            <Project v-for="project in filteredProjects" :project="project" :key="project.id"/>
        </section>
    </div>
</template>