<script setup>
import Hero from '@/Components/Frontend/Hero.vue';
import Frontend from '@/Layouts/Frontend.vue';
import { Head, Link } from '@inertiajs/vue3';
import Promote from '@/Components/Frontend/Promote.vue';
import Skills from '@/Components/Frontend/Skills.vue';
import Portfolio from '@/Components/Frontend/Portfolio.vue';
import Contacts from '@/Components/Frontend/Contacts.vue';

defineProps({
    skills: {
        type: Object,
    },
    projects: {
        type: Object
    }
});
</script>

<template>
    <Head title="Welcome" />

    <Frontend>

        <Hero/>

        <Promote/>

        <Skills :skills="skills"/>

        <Portfolio :skills="skills" :projects="projects"/>

        <Contacts/>

    </Frontend>
</template>

<style>
</style>
