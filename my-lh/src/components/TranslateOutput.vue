<template>
  <div id="translateOutput">
    <h2>{{translatedText}}</h2>
    <!--console.log(translateText)-->
  </div>
</template>

<script>


  export default {
    name: 'translateOutput',
    props: [
      "translatedText"
    ]
  }
</script>

<style>
#translateOutput h2 {
  border: 1px solid #999;
  width: 300px;
  height: 200px;
}
</style>
