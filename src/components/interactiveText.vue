<template>
    <div class="container">
        <div id="panel">
            <button v-on:click="isBold = !isBold"><Strong>B</Strong></button>
            <button v-on:click="isItalic = !isItalic"><i>I</i></button>
            <button v-on:click="isUnderline = !isUnderline" class="textDecorationUnderline">U</button>

            <select v-model="colorSelected">
                <option disabled value="">Выберет цвет</option>
                <option v-for="color in colors" v-bind:key="color.id">{{color}}</option>
            </select>
            <select v-model="fontSelected">
                <option disabled value="">Выберет шрифт</option>
                <option v-for="font in fonts" v-bind:key="font.id">{{font}}</option>
            </select>
        </div>
        <div id="textField">
            <textarea
                    :class="[
                    {lengthString: isActiveLengthString},
                    weightFont,
                    styleFont,
                    decorationFont
                    ]"
                    :style="[colorFont, familyFont]"
                    v-on:keyup.enter="heightLimit"
                    v-on:keyup.delete="reduceLimit"
                    v-model="value"
                    v-bind:[rows]="numberLines"
            ></textarea>
        </div>
        <div>
            <h2>Счетчик строк = {{numberLines}}</h2>
        </div>
    </div>
</template>
<script>
    export default {
        name: 'interactiveText',
        data: () => ({
            isBold: false,
            isItalic: false,
            isUnderline: false,
            rows: 'rows',
            resize: 'none',
            counter: 1,
            text: '',
            value: 'Стандартный текст',
            numberLines: 1,
            isActiveLengthString: true,
            colorSelected: '',
            fontSelected: '',
            colors: [
                'black',
                'yellow',
                'red',
                'blue'
            ],
            fonts: [
                'Arial',
                'Times New Roman',
                'Verdana',
                'Georgia'
            ]
        }),

        methods: {
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
        },
        computed: {
            weightFont: function () {
                return {
                    'textWeightBold': this.isBold,
                    'textWeightNormal': !this.isBold
                }
            },
            styleFont: function () {
                return {
                    'textStyleItalic': this.isItalic,
                    'textStyleNormal': !this.isItalic
                }
            },
            decorationFont: function () {
                return {
                    'textDecorationUnderline': this.isUnderline,
                    'textDecorationNormal': !this.isUnderline
                }
            },
            colorFont: function () {
                return {
                    'color': this.colorSelected
                }
            },
            familyFont: function () {
                return {
                    'font-family': this.fontSelected
                }
            },
        }
    }
</script>

<style>
    .container {
        margin: 0 auto;
        width: 450px;
    }

    #panel {
        float: left;
    }

    #textField {
        float: left;
    }

    .lengthString {
        width: 400px;
    }

    .body {
        margin: 0 auto;
    }

    .lengthString {
        resize: none;
    }

    .textWeightBold {
        font-weight: bold;
    }

    .textWeightNormal {
        font-weight: normal;
    }

    .textStyleItalic {
        font-style: italic;
    }

    .textStyleNormal {
        font-style: normal;
    }

    .textDecorationUnderline {
        text-decoration: underline;
    }

    .textDecorationNormal {
        text-decoration: none;
    }
</style>