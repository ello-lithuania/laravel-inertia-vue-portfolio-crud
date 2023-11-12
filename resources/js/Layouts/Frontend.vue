<script setup>
import Header from '@/Components/Frontend/Header.vue';
import Footer from '@/Components/Frontend/Footer.vue';

</script>

<template>
    <div class="bg-white dark:bg-white">

        <Header/>

        <main class="min-h-screen">
            <slot/>
        </main>

        <Footer/>
    </div>
</template>