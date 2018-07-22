<template>
    <div id="app">
        <offline @detected-condition="handleConnectivityChange"/>
        <div v-if="!isOnline">
            <p class="top-alert"><strong>Offline</strong> detected. Please don't reload your window.</p>
        </div>
        <div id="nav">
            <router-link to="/">Home</router-link>
            |
            <router-link to="/about">About</router-link>
        </div>
        <router-view/>
    </div>
</template>

<script>
    import offline from 'v-offline';

    export default {
        name: "App",
        data() {
            return {
                isOnline: true,
            }
        },
        components: {
            offline
        },
        methods: {
            handleConnectivityChange(status) {
                this.isOnline = status;
                window.isOnline = status;
            }
        },
        mounted() {

        }
    }
</script>

<style>
    #app {
        font-family: 'Avenir', Helvetica, Arial, sans-serif;
        -webkit-font-smoothing: antialiased;
        -moz-osx-font-smoothing: grayscale;
        text-align: center;
        color: #2c3e50;
    }

    #nav {
        padding: 30px;
    }

    #nav a {
        font-weight: bold;
        color: #2c3e50;
    }

    #nav a.router-link-exact-active {
        color: #42b983;
    }
    .top-alert {
        background-color: #f7d438;
        padding: 10px;
        margin-top: 0;
    }
</style>
