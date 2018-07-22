<template>
    <div class="home">
        <h1>Meet the Dogs</h1>
        <dog-list/>
    </div>
</template>

<script>
    import DogList from '../components/DogList'

    export default {
        name: 'home',
        components: {
            DogList
        }
    }
</script>
