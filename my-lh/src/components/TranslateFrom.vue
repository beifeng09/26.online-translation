<template>
  <div class="row" id="translateFrom">
    <div class="col-md-6 col-md-offset-3">
      <form id="transForm" class="well form-inline" v-on:submit="formSubmit">
        <input class="form-control" type="text" v-model="textToTranslate" placeholder="请输入需要翻译的内容">

      <select v-model="language" class="form-control">
        <option value="en">英语</option>
        <option value="zh">中文</option>
        <option value="ja">日语</option>
        <option value="ko">朝鲜</option>
        <option value="ru">俄语</option>
        <option value="ar">阿拉伯</option>

      </select>
      <input class="btn btn-primary" type="submit" value="翻译">
      </form>
    </div>
  </div>
</template>

<script>


  export default {
    name: 'translateFrom',
    data:function(){
      return {
        textToTranslate:"",
        language:""
      }
    },
    methods: {
      formSubmit:function (e) {
        // alert(this.textToTranslate);
        //1.传递参数
        this.$emit("formSubmit",this.textToTranslate,this.language);
        e.preventDefault();

      }
    },
    //默认语言被选中
    created:function() {
      this.language = "en";
    }

  }
</script>

<style>
#transForm {
  body: 1px solid #ccc;
  border-radius: 10px;
}
</style>
