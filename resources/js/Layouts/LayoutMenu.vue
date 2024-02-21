<template>
    <div>
        <Link class="bg-green-500 text-white px-4 py-2 rounded hover:bg-green-700 transition duration-300"
            :href="route('home')" :class="{'font-bold': $page.url === '/home'}">Posts</Link>
        <Link class="bg-green-500 text-white px-4 py-2 rounded hover:bg-green-700 transition duration-300 ml-4"
            :href="route('about')" :class="{'font-bold': $page.url === '/about', 'bg-red-500': $page.url === '/about', 'bg-blue-500': $page.url !== '/about'}">Sobre</Link>
    </div>
</template>

<script>
    import { Link } from '@inertiajs/vue3';

    export default {
        name: 'LayoutMenu',

        components: {
            Link
        }
    }
</script>

<style lang="css" scoped>

</style>
