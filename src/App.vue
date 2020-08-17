<template>
    <div class="text-center" id="app">
        <h1>Vue Translator</h1>
        <TranslateForm @formSubmit="translateText"></TranslateForm>
        <TranslateOutput :translatedText="translatedText"></TranslateOutput>
    </div>
</template>

<script>

import TranslateForm from './components/TranslateForm';
import TranslateOutput from './components/TranslateOutput';

import axios from "axios";

export default {

    components: {
        TranslateForm,
        TranslateOutput
    },

    data: function() {
        return {
            translatedText: '',
            yandexTranslateKey: ''

        }
    },

    methods: {
        translateText: function(text, language) {
            axios.get('https://translate.yandex.net/api/v1.5/tr.json/translate?key='+this.yandexTranslateKey+'&lang='+language+'&text='+text)
                .then((response) => {
                    console.log(response);
                    this.translatedText = response.data.text[0];
                });
        }
    }

}
</script>

<style lang="stylus">
body
    background #fefefe
    #app
        font-family Avenir, Helvetica, Arial, sans-serif
        -webkit-font-smoothing antialiased
        -moz-osx-font-smoothing grayscale
        textarea
            resize none
            max-width 300px
            margin 0 auto 20px auto
        select
            max-width 300px
            margin 0 auto 20px auto
        p
            max-width 300px
            margin 0 auto
            min-height 20px
</style>