<template>
    <div>
        <button v-on:click="stopFetch=true">{{ btnText }}</button>
        <br/>
        <div v-for="photo in dogs" style="display: inline">
            <img :src="photo" :width="300">
        </div>
    </div>
</template>


<script>
    export default {
        name: 'DogList',
        data() {
            return {
                dogs: [],
                stopFetch: false,
                btnText: 'Stop Feching'
            }
        },
        methods: {
            getRandomDog() {
                fetch('https://dog.ceo/api/breeds/image/random').then(function(response){
                    return response.json()
                }).then(data => {
                    if (data.status === 'success') {
                        this.dogs.unshift(data.message)
                    }
                })
            }
        },
        mounted() {
            setInterval( ()=> {
                if(!this.stopFetch && window.isOnline) {
                    this.getRandomDog()
                }
            }, 3000);
            // console.log(this.isOnline);
        },
        watch: {
            stopFetch(newVal, oldVal) {
                if (newVal) {
                    this.btnText = 'Start Fetching'
                }
            }
        }
    }
</script>


<style>

</style>