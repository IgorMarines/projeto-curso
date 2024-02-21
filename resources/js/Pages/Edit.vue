<template>
    <Head>
        <title>Edit post</title>
    </Head>
    <AppLayout title="Dashboard">
        <template #header>
            <h2 class="font-semibold text-xl text-gray-800 leading-tight">
                Edit Post
            </h2>
        </template>

        <div class="py-12">
            <div class="max-w-7xl mx-auto sm:px-6 lg:px-8">
                <form @submit.prevent="form.put(route('dashboard.update', form.id))">
                    <div class="mb-4">
                        <label for="title" class="block text-sm font-medium text-gray-600">Título:</label>
                        <input v-model="form.title" type="text" id="title" name="title"
                            class="mt-1 p-2 border rounded-md w-full">
                    </div>

                    <div class="mb-4">
                        <label for="content" class="block text-sm font-medium text-gray-600">Conteúdo:</label>
                        <textarea v-model="form.content" id="content" name="content" rows="4"
                            class="mt-1 p-2 border rounded-md w-full"></textarea>
                    </div>

                    <button type="submit"
                        class="bg-blue-500 text-white px-4 py-2 rounded hover:bg-blue-700 transition duration-300">Enviar</button>
                </form>
            </div>
        </div>
    </AppLayout>
</template>

<script setup>
import AppLayout from '@/Layouts/AppLayout.vue';
import { Head, Link, useForm } from '@inertiajs/vue3';


</script>

<script>
export default {
    props: {
        post: Object,
        errors: Object
    },

    components: {
        Link,
        Head,
    },

    data(props) {
        const form = useForm(props.post);

        return {
            form
        }
    }
}
</script>
