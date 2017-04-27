<template lang="html">
  <div class="col-md-9 col-md-offset-3 col-sm-8 col-sm-offset-4">
    <p id="translated">{{translatedWord}}</p>

  </div>
</template>

<script>
export default {
  props:['translatedWord'],
  data(){
    return{

    }
  }

}
</script>

<style lang="css">
  #translated{
    font-size: 25px;
    padding-top: 50px;
  }
</style>
