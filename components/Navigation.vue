<template>
    <nav>
        <nuxt-link to="/"><h1>Qualtrax</h1></nuxt-link>
        <ul>
            <li><nuxt-link to="/documents">Documents</nuxt-link></li>
            <li><nuxt-link to="/users">Users</nuxt-link></li>
        </ul>
    </nav>
</template>

<style>
nav {
    font-size: 1.5rem;
    padding: 1rem;
}
ul {
    margin: 0;
    margin-top: 1rem;
    padding: 0;
    list-style: none;
}
</style>