<script  setup>
import AppLayout from '@/Layouts/AppLayout.vue';
</script>
<script>

import { Link, router } from '@inertiajs/vue3'
// import { Inertia } from '@inertiajs/inertia';


export default {
    props: {
        posts: Object
    },
    components: {
        Link,
        AppLayout
    },
    data() {
        const destroy = (id) => {
            if(confirm('certeza que deseja excluir esse post')){
                router.delete(route('dashboard.destroy', id))
            }
        }

        return  {
            destroy
        }
    },
}
</script>


<template>
    <AppLayout title="Dashboard">
        <template #header>
            <h2 class="font-semibold text-xl text-gray-800 leading-tight">
                Listagem de Posts - Olá {{ $page.props.user.name }}
            </h2>
        </template>

        <div class="py-12">
            <div class="max-w-7xl mx-auto sm:px-6 lg:px-8">
                <div class="py-8 bg-white overflow-hidden shadow-xl sm:rounded-lg">
                    <Link :href="route('dashboard.create')">
                        <button class="ml-4 bg-blue-500 text-white px-4 py-2 rounded hover:bg-blue-700 transition duration-300"
                            @click="criarNovoPost">
                            Criar Novo Post
                        </button>
                        <div v-if="$page.props.flash.message" class="text-blue-600">
                            {{ $page.props.flash.message }}
                        </div>
                    </Link>
                    <div class="overflow-x-auto mt-4">
                        <table class="min-w-full border border-gray-300">
                            <thead>
                                <tr>
                                    <th class="py-2 px-4 border-b">ID</th>
                                    <th class="py-2 px-4 border-b">Título</th>
                                    <th class="py-2 px-4 border-b">Conteúdo</th>
                                    <th class="py-2 px-4 border-b">Ações</th>
                                </tr>
                            </thead>
                            <tbody>
                                <tr v-for="post in posts" :key="post.id">
                                    <td class="py-2 px-4 border-b">{{ post.id }}</td>
                                    <td class="py-2 px-4 border-b">{{ post.title }}</td>
                                    <td class="py-2 px-4 border-b">{{ post.content }}</td>
                                    <td class="py-2 px-4 border-b">
                                        <Link :href="route('dashboard.edit', post.id)" class="ml-4 bg-yellow-500 text-white px-2 w-[80%] py-2 rounded hover:bg-yellow-700 transition duration-300">Editar</Link>
                                        <button
                                            @click="destroy(post.id)"
                                            class="ml-4 bg-red-500 text-white px-2 w-[80%] mt-1 py-2 rounded hover:bg-red-700 w-[80%] transition duration-300">Apagar</button>
                                    </td>

                                </tr>
                            </tbody>
                        </table>
                    </div>
                </div>
            </div>
        </div>
    </AppLayout>
</template>
