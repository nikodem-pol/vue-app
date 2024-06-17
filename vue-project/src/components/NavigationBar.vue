<script setup>
import { onMounted, ref } from 'vue';

const loggedIn  = ref(true);

</script>

<template>
    <div class="navbar">
        <p>Collaborative Whiteboard</p>
        <div class="nav-buttons" v-if="loggedIn">
            <RouterLink class="a" to="/">Dashboard</RouterLink>
            <RouterLink to="/">Settings</RouterLink>
            <RouterLink to="/">About</RouterLink>
        </div>
        <button>{{ loggedIn ? "Sign out" : "Sign in" }}</button>
    </div>
</template>

<style scoped>
    .navbar {
        display: grid;
        grid-template-columns: repeat(5, 1fr);
        position: fixed;
        width: 100%;
        min-height: 10vh;
        top: 0;
        left: 0;
        right: 0;
        margin-top: 0;
        background-color: rgb(47, 54, 94);
        align-items: center;
        padding: 0 15px;
        z-index: 2;
    }

    p {
        color: white;
    }

    button {
        grid-column: 5;
        display: block;
        justify-self: end;
        background-color: white;
        height: 2.5em;
        width: 6em;
        border: none;
        border-radius: 1em;
    }

    .nav-buttons {
        display: flex;
        grid-column: 2 / 5;
        justify-content: flex-start;
    }

    .nav-buttons a {
        color: white;
        text-decoration: none;
        padding: 1em;
        border-bottom: 3px solid transparent;
    }

    .nav-buttons a:hover {
        background-color: rgb(41, 47, 83);
        border-bottom: 3px solid  rgb(26, 30, 53);
    }
</style>