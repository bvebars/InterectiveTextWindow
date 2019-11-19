<template>
    <div class="hello">
        <h1>{{ msg }}</h1>
    </div>
</template>

<script>
    export default {
        name: 'HelloWorld',
        props: {
            msg: String
        }
    }
</script>

v-bind:class="{
lengthString: isActiveLengthString,
textItalic: isActiveItalic,
textUnderline: isActiveTextUnderline,
}"
