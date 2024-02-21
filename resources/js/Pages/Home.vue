<template>

  <Head>
    <title>Postagens</title>
  </Head>
  <div class="container mx-auto p-4">
    <MenuLayout/>
    <hr class="mt-5" />
    <h1 class="text-2xl font-bold mb-4">Lista de postagens</h1>   
    
    <!-- Botão para criar um novo post -->
    <button class="bg-blue-500 text-white px-4 py-2 rounded hover:bg-blue-700 transition duration-300"
    @click="criarNovoPost">
    Criar Novo Post
  </button>
  
  <div class="overflow-x-auto mt-4">
            <table class="min-w-full border border-gray-300">
                <thead>
                    <tr>
                        <th class="py-2 px-4 border-b">ID</th>
                        <th class="py-2 px-4 border-b">Título</th>
                        <th class="py-2 px-4 border-b">Conteúdo</th>
                    </tr>
                </thead>
                <tbody>
                    <tr v-for="post in posts" :key="post.id">
                        <td class="py-2 px-4 border-b">{{ post.id }}</td>
                        <td class="py-2 px-4 border-b">{{ post.title }}</td>
                        <td class="py-2 px-4 border-b">{{ post.content }}</td>
                    </tr>
                </tbody>
            </table>
        </div>
    </div>
</template>
  
<script>
import { Link, Head } from '@inertiajs/vue3'

import MenuLayout from '../Layouts/LayoutMenu.vue'

export default {

    name: 'PageHome',

    components: {
    Link,
    MenuLayout,
    Head
},
    props: {
        posts: Object
    },
    methods: {
        criarNovoPost() {
            // Lógica para criar um novo post
            alert('Novo post criado!');
        }
    }
}
</script>
  
<style lang="css" scoped>
/* Adicione estilos adicionais aqui, se necessário */
</style>
  