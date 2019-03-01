<template>
  <div id="app" class="text-center">
   <div class="container">
    <h1>Word Translator</h1>
    <hr>
    <TranslateForm v-on:formSubmit="translateText"></TranslateForm>
    <TranslateOutput v-text="translatedText"></TranslateOutput>
  </div>
  </div>
</template>

<script>
import TranslateForm from './components/TranslateForm'
import TranslateOutput from './components/TranslateOutput'

export default {
  name: 'App',
  components: {
    TranslateForm,
		TranslateOutput
  },
  data: function(){
    return {
      translatedText: ''
    }
  },
  methods: {
    translateText: function(text, language){
      this.$http.get('https://translate.yandex.net/api/v1.5/tr.json/translate?key=trnsl.1.1.20190228T222857Z.f807c6de071bbd02.65da427ee106ea48df5f2a03bfb2c764bf6761fa&lang='+language+'&text='+text)
      .then((response) => {
        this.translatedText = response.body.text[0]
      })
    }
  }
}
</script>

<style>
  body {
    background-color: #e3dfff;
    padding: 20px;
  }
</style>
