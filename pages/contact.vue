<template>
  <div class="gridContainer__element">
    <h2>Ich bin unter folgenden Social-Media-Acounts erreichen:</h2> 
    <div class="contact__linklist">
      <Links v-for="(item, index) in data" :key="index" :data="item"/>
    </div>
  </div>
</template>

<script>
  export default {
    layout: 'defaultLayout',
    data() {
        let data = [{
            name:"facebook",
            url:"Johanna Kraken",
            link:"/"
        },{
            name:"linkedin",
            url:"www.linkedin.com/in/johannakraken/",
            link:"/"
        }];

        return {data:data};
    }
  }
</script>

<style lang="scss" scoped>
  .contact__linklist {
    display: grid;
  }
</style>
