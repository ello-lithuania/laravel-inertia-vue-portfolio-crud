<template>
    <Head title="Skills index" />

    <AuthenticatedLayout>
        <template #header>
            <h2 class="font-semibold text-xl text-gray-800 leading-tight">New Project</h2>
        </template>

        <div class="py-12">
            <div class="max-w-md mx-auto sm:px-6 lg:px-8 bg-white">

                <form class="p-4 mt-2" @submit.prevent="submit">

                    <div>
                        <InputLabel for="skill_id" value="Choose skill" />
                        <select v-model="form.skill_id" class="w-full" name="skill_id" id="skill_id">
                            <option v-for="skill in skills" :key="skill.id" :value="skill.id">{{ skill.name }}</option>
                        </select>

                        <InputError class="mt-2" :message="form.errors.skill_id" />
                    </div>

                    <div>
                        <InputLabel for="name" value="Name" />

                        <TextInput
                            id="name"
                            type="text"
                            class="mt-1 block w-full"
                            v-model="form.name"
                            autofocus
                            autocomplete="name"
                        />

                        <InputError class="mt-2" :message="form.errors.name" />
                    </div>

                    <div>
                        <InputLabel for="project_url" value="URL" />

                        <TextInput
                            id="project_url"
                            type="text"
                            class="mt-1 block w-full"
                            v-model="form.project_url"
                            autocomplete="project_url"
                        />

                        <InputError class="mt-2" :message="form.errors.project_url" />
                    </div>

                    <div>
                        <InputLabel for="image" value="Image" />

                        <TextInput
                            id="image"
                            type="file"
                            class="mt-1 block w-full"
                            @input="form.image = $event.target.files[0]"
                        />

                        <InputError class="mt-2" :message="form.errors.image" />
                    </div>

                    <div class="flex items-center justify-end mt-4">

                        <PrimaryButton class="ms-4" :class="{ 'opacity-25': form.processing }" :disabled="form.processing">
                            Save project
                        </PrimaryButton>
                    </div>
                </form>

            </div>
        </div>
    </AuthenticatedLayout>
</template>

<script setup>
import AuthenticatedLayout from '@/Layouts/AuthenticatedLayout.vue';
import InputError from '@/Components/InputError.vue';
import InputLabel from '@/Components/InputLabel.vue';
import PrimaryButton from '@/Components/PrimaryButton.vue';
import TextInput from '@/Components/TextInput.vue';
import { Head, Link, useForm } from '@inertiajs/vue3';

const form = useForm({
    name: '',
    image: null,
    skill_id: '',
    project_url: ''
});

defineProps({
    skills: {
        type: Array,
    },
});

const submit = () => {
    form.post(route('projects.store'));
};
</script>