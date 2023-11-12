<script setup>
import { ref } from 'vue';
import { useForm } from '@inertiajs/vue3';

const showMessage = ref(false);

const form = useForm({
    name: '',
    email: '',
    body: ''
})

function setShowMessage(value) {
    showMessage.value = value
}

function cleanForm() {
    form.reset()
    setShowMessage(true)
    setTimeout(() => setShowMessage(false), 2000)
}

const submit = () => {
    form.post(route('contact'), {
        preserveScroll: true,
        onSuccess: () => cleanForm()
    })
}
</script>

<template>

    <section id="#contact" class="section bg-light dark:bg-dark-primary">
        <div class="container mx-auto">
            <div class="flex flex-col items-center text-center">
                <h2 class="section-title text-black">Contact me</h2>
                <p class="subtitle">Lorem ipsum dolor sit amet consectetur, adipisicing elit. Natus amet, rem eius cum eligendi minima eum neque esse delectus quis molestiae voluptatem? Ut voluptatum ipsa dolore corrupti laboriosam eligendi officiis.</p>
            </div>
            <div class="flex flex-col lg:flex-row lg:gap-x-8">
                <div class="flex flex-1 flex-col items-start space-y-8 mb-12 lg:mb-0 lg:pt-2">
                    <div class="flex flex-col lg:flex-row gap-x-4">
                        <div></div>
                        <div>
                            <h4 class="text-xl mb-1 text-black">Have a question?</h4>
                            <p class="mb-1">I am here to help you</p>
                        </div>
                    </div>
                </div>
                <form @submit.prevent="submit" class="space-y-8 w-full max-w-md">
                    <div v-if="showMessage" class="m-2 p-4 bg-light-tail-500 dark:bg-dark-navy-100 rounded-lg">
                        Thank you for your message.
                    </div>
                    <div class="flex gap-8">
                        <div>
                            <input v-model="form.name" type="text" class="input" placeholder="Name"/>
                            <span v-if="form.errors.name" class="text-sm m-2 text-red-400">{{ form.errors.name }}</span>
                        </div>
                        <div>
                            <input v-model="form.email" type="email" class="input" placeholder="Email"/>
                            <span v-if="form.errors.email" class="text-sm m-2 text-red-400">{{ form.errors.email }}</span>
                        </div>
                    </div>
                    <textarea v-model="form.body" class="textarea" placeholder="Message" spellcheck="false"></textarea>
                    <span v-if="form.errors.body" class="text-sm m-2 text-red-400">{{ form.errors.body }}</span>

                    <button class="btn btn-lg hover:bg-secondary text-white bg-blue-700">
                        Send message
                    </button>
                </form>
            </div>
        </div>
    </section>

</template>