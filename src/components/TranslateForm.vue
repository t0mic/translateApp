<template lang="html">
  <div class="">
    <form class="form-inline">
      <input type="text" placeholder="Translate Word" class="form-control" v-model="translateWord">
      <select class="form-control" v-model="language">
        <option value="ru">Russian</option>
        <option value="sr">Serbian</option>
        <option value="de">German</option>
        <option value="pl">Polish</option>
        <option value="es">Spanish</option>
        <option value="zh">Chinese</option>
      </select>
      <input type="submit" value="Translate" class="form-control" @click="formSend">
    </form>
  </div>
</template>

<script>
export default {
  data(){
    return{
      translateWord: "",
      language: ""
    }
  },
  created(){
    this.language = 'ru';
  },
  methods: {
    formSend(e){
      e.preventDefault();
      this.$emit('form-submit', this.translateWord, this.language);
    }
  }

}
</script>

<style lang="css">
</style>
