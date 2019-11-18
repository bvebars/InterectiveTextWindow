<template>
    <div id="app">
        <HelloWorld msg="Интерактивное окно с текстом"/>
        <interactiveText/>
    </div>
</template>

<script>
    import HelloWorld from './components/HelloWorld'
    import interactiveText from './components/interactiveText'
    export default {
        name: 'app',
        components: {
            HelloWorld,
            interactiveText
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
        margin-top: 60px;
    }
</style>