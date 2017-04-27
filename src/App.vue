<template>
  <div class="container">
    <h1 class="text-center">Word Translator</h1>
    <p class="text-center">Powered By Vue.js</p>
    <appTranslateForm v-on:form-submit="translateText"></appTranslateForm>
    <appTranslateOutput :translatedWord="translatedWord">{{translatedWord}}</appTranslateOutput>
  </div>
</template>

<script>
import TranslateForm from './components/TranslateForm.vue'
import TranslateOutput from './components/TranslateOutput.vue'
export default {
  name: 'app',
  data () {
    return {
      translatedWord: ''
    }
  },
  components:{
    appTranslateForm: TranslateForm,
    appTranslateOutput: TranslateOutput
  },
  methods:{
    translateText(text, language){
      console.log(text);
      this.$http.get('https://translate.yandex.net/api/v1.5/tr.json/translate?key=trnsl.1.1.20170425T201904Z.2d86690769d8a9a3.931637966c2102f51909f2b63a00adfac673e81e&lang='+language+'&text='+text)
      .then((response) => {
        this.translatedWord = response.body.text[0];
      })
    }
  }
}
</script>

<style>

</style>
