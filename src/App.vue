<template>
  <div id="app">
    <h1>在线翻译</h1>
    <h5>简单/易用/便捷</h5>
    <TranslateForm v-on:formSubmit="translateText"></TranslateForm>
    <TranslateOutput v-text="translatedText"/>
  </div>
</template>

<script>
import TranslateForm from "./components/TranslateForm"
import TranslateOutput from "./components/TranslateOutput"
export default {
  name: 'app',
  data(){
    return{
      translatedText:""
    }
  },
  methods:{
    translateText:function(text,language){
      this.$http.get('https://translate.yandex.net/api/v1.5/tr.json/translate?key=trnsl.1.1.20180127T163243Z.eeedf387ebdde5ea.29a8b8e3afa14f21cb1e9f6a3a133030fe93c2dd&lang='+language+'&text='+text).then((responce)=>{
        console.log(responce);
        // this.translatedText=responce.body.text[0];
      })
    }
  },
  components:{
    TranslateForm,
    TranslateOutput
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
