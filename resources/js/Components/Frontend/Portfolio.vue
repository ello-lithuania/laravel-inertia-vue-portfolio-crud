<script setup>
import Projects from './Projects.vue';

defineProps({
    skills: {
        type: Object
    },
    projects: {
        type: Object
    }
})
</script>

<template>

    <section id="#portfolio" class="section bg-light dark:bg-blue-700 min-h-[1400px]">
        <div class="container mx-auto">
            <div class="flex flex-col items-center text-center">
                <h2 class="section-title">My latest work</h2>
                <p class="subtitle">Lorem ipsum dolor sit amet consectetur adipisicing elit. Quaerat, in eos. Nostrum architecto dolore accusamus est iure quae qui, totam nemo incidunt necessitatibus amet autem, voluptatem nam, sed sit quidem?</p>
            </div>
        </div>
        <Projects :skills="skills" :projects="projects"/>
    </section>

</template>