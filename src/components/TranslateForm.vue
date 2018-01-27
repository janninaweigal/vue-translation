<template>
  <div id="translateForm">
    <form v-on:submit="formSubmit">
        <input type="text" v-model="textToTranslate" placeholder="输入需要翻译的内容">
        <select>
            <option value="en">English</option>
            <option value="ru">Russian</option>
            <option value="ko">Korean</option>
            <option value="ja">Janpenese</option>
        </select>
        <input type="submit" value="翻译">
    </form>
  </div>
</template>

<script>
export default {
  name: 'translateForm',
  data(){
      return {
          textToTranslate:"",
          language:""
      }
  },
  methods:{
      formSubmit:function(e){
          e.preventDefault();
          this.$emit("formSubmit",this.textToTranslate,this.language);
      }
  },
  created:function(){
      this.language="en";
  }
}
</script>

<style>

</style>
