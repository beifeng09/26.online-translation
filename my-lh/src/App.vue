<template>
  <div id="app">

    <h1>在线翻译！</h1>
    <h5 class="text-muted">简单/易用/便捷</h5>
<translateFrom v-on:formSubmit="translateText"></translateFrom>
    <translateOutput class="id" v-text="translatedText"></translateOutput>


  </div>
</template>

<script>
import TranslateFrom from './components/TranslateFrom';
import TranslateOutput from './components/TranslateOutput'

export default {
  name: 'App',
  data:function() {
    return{
      //已经翻译好
      translatedText:""
    }

  },
  components: {
    TranslateFrom, TranslateOutput

  },
  methods: {
    //2.接收数据
    translateText:function(text,language) {
      // alert(text);
      //获取翻译API 参值 语言
      this.$http.get('https://translate.yandex.net/api/v1.5/tr.json/translate?key=trnsl.1.1.20190423T033159Z.65777de77924679e.4cbabca43687874212a792cd0415a053fb1e6d98&lang='+language+'&text='+text)
        //返回值
        .then((response) => {
          //输出Response -->body-->text
          // console.log(response.body.text);
          this.translatedText = response.body.text[0];
        })
    }
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
