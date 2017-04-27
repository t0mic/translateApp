<template>
  <div class="container">
    <h1 class="text-center">Word Translator</h1>
    <p class="text-center"><a id="yandex" href="http://translate.yandex.com/" target="blank">Powered by Yandex.Translate</a></p>
    <hr>
    <appTranslateForm v-on:form-submit="translateText"></appTranslateForm>
    <appTranslateOutput :translatedWord="translatedWord"></appTranslateOutput>
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
      let encoded = encodeURI(text);
      this.$http.get('https://translate.yandex.net/api/v1.5/tr.json/translate?key=trnsl.1.1.20170425T201904Z.2d86690769d8a9a3.931637966c2102f51909f2b63a00adfac673e81e&lang='+language+'&text='+encoded)
      .then((response) => {
        this.translatedWord = response.body.text[0];
      })
    }
  }
}
</script>

<style lang="css">
  p{
    padding-bottom: 25px;
  }
  #yandex{
    color: inherit;
  }
  #yandex:hover{
    text-decoration: none;
  }
</style>
