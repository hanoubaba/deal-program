<template>
    <div id="app">
        <HelloWorld msg="" />
    </div>
</template>

<script>
// import HelloWorld from './components/HelloWorld.vue'
import HelloWorld from './components/bdemo.vue'

export default {
    name: 'App',
    components: {
        HelloWorld
    }
}
</script>

<style>
#app {
    font-family: Avenir, Helvetica, Arial, sans-serif;
    -webkit-font-smoothing: antialiased;
    -moz-osx-font-smoothing: grayscale;
    text-align: center;
    color: #2c3e50;
    /* margin-top: 60px; */
    margin: 0;
    padding: 0;
}
</style>
