<script setup>
defineProps({
    skills: {
        type: Object
    }
})
</script>

<template>

    <section id="#skills" class="bg-light dark:bg-dark-navy-500 py-12">
        <div class="container mx-auto">
            <div class="grid grid-cols-8 md:grid-flow-col">
                <div class="flex items-center justify-center" v-for="skill in skills.data" :key="skill.id">
                    <img :src="skill.image" :alt="skill.name" class="lg:h-20"/>
                </div>
            </div>
        </div>
    </section>

</template>