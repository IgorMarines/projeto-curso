<template>
    <Head>
        <title>Sobre</title>
    </Head>
    <h1>Estou na pagina about</h1>
    <h2>{{ name }}</h2>
    <h3>Estou no curso de: {{ curso }}</h3>
    <menu-layout/>
</template>

<script>
    import MenuLayout from '../Layouts/LayoutMenu.vue'
    import { Head, Link } from '@inertiajs/vue3';
export default {
    name: 'PageAbout',

    components: {
    Link,
    MenuLayout,
    Head
},

    props: {
        name: String,
        curso: String
    }
}
</script>