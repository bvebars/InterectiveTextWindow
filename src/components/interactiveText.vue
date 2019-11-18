<template>
    <div class="container">
        <div id="panel">
            <button v-on:click="textBold"><Strong>B</Strong></button>
            <button v-on:click="textItalic"><i>I</i></button>
            <button class="textUnderline" v-on:click="textUnderline">U</button>
            <button v-on:click="textItalic">Выбор шрифта</button>
            <select v-model="selected">
                <option disabled value="">Выберет цвет</option>
                <option v-for="color in colors" v-bind:key="color.id">{{color}} </option>
            </select>
        </div>
        <div id="textField">
            <textarea
                    v-bind:class="{
                    lengthString: isActiveLengthString,
                    textBold: isActiveBold,
                    textItalic: isActiveItalic,
                    textUnderline: isActiveTextUnderline}"
                    v-on:keyup.enter="heightLimit"
                    v-on:keyup.delete="reduceLimit"
                    v-model="value"
                    v-bind:[rows]="numberLines"
            ></textarea>
        </div>
        <h2>Счетчик строк  = {{numberLines}}</h2>
    </div>
</template>
<script>
    export default {
        name: 'interactiveText',
        data: () => ({
            rows: 'rows',
            resize: 'none',
            counter: 1,
            text: '',
            value: '',
            numberLines: 1,
            isActiveLengthString: true,
            isActiveBold: false,
            isActiveItalic: false,
            isActiveTextUnderline: false,
            selected: '',
            colors: [
                'black',
                'yellow',
                'red',
                'blue'
            ]
        }),

        methods: {
            textBold: function () {
                this.isActiveBold = true;
            },
            textItalic: function () {
                this.isActiveItalic = true;
            },
            textUnderline: function () {
                this.isActiveTextUnderline = true;
            },
            heightLimit: function () {
                if (this.value.split("\n").length > 10) {
                    return
                }
                this.numberLines = this.value.split("\n").length
            },
            reduceLimit: function () {
                if (this.value.split("\n").length < 10) {
                    this.numberLines = this.value.split("\n").length
                }
            }


        }
    }
</script>

<style>
    .lengthString {
        width: 400px;
    }

    .body {
        margin: 0 auto;
    }

    .lengthString {
        resize: none;
    }

    .textBold {
        font-weight: bold;
    }

    .textItalic {
        font-style: italic;
    }

    .textUnderline {
        text-decoration: underline;
    }

</style>