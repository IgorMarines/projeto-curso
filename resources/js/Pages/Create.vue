<template>
    <Head>
        <title>Novo post</title>
    </Head>
    <AppLayout title="Dashboard">
        <template #header>
            <h2 class="font-semibold text-xl text-gray-800 leading-tight">
                Novo Post
            </h2>
        </template>

        <div class="py-12">
            <div class="max-w-7xl mx-auto sm:px-6 lg:px-8">
                <form @submit.prevent="form.post(route('dashboard.store'))">
                    <div class="mb-4">
                        <label for="title" class="block text-sm font-medium text-gray-600">Título:</label>
                        <input v-model="form.title" type="text" id="title" name="title" class="mt-1 p-2 border rounded-md w-full">
                    </div>

                    <p class="text-red-500" v-if="errors.title">{{ errors.title }}</p>
                    
                    <div class="mb-4">
                        <label for="content" class="block text-sm font-medium text-gray-600">Conteúdo:</label>
                        <textarea v-model="form.content" id="content" name="content" rows="4" class="mt-1 p-2 border rounded-md w-full"></textarea>
                    </div>
                    
                    <p class="text-red-500" v-if="errors.content">{{ errors.content }}</p>
                    <button type="submit" class="bg-blue-500 text-white px-4 py-2 rounded hover:bg-blue-700 transition duration-300">Enviar</button>
                </form>
            </div>
        </div>
    </AppLayout>
</template>

<script>

import { Link, Head, useForm } from '@inertiajs/vue3';
import AppLayout from '@/Layouts/AppLayout.vue';

export default {
    props: {
        posts: Object,
        errors: Object
    },

    components: {
        Link,
        Head,
        AppLayout
    },

    data() {
        const form = useForm({
            title: '',
            content: ''
        })

        return {
            form
        }
    }
}
</script>
