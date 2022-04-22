<template>
  <div class="gridContainer__element">
    <h1>Ich bin unter folgenden Social-Media-Acounts erreichen:</h1> 
    <div class="contact__linklist">
      <Links v-for="(item, index) in data" :key="index" :type="svg" :data="item"/>
    </div>
  </div>
</template>

<script>
  export default {
    layout: 'defaultLayout',
    data() {
        let data = [{
            name:"facebook.png",
            url:"",
            link:"https://www.facebook.com/johanna.kraken",
            target:"_blank"
        },{
            name:"linkedin.png",
            url:"",
            link:"www.linkedin.com/in/johannakraken/",
            target:"_blank"
        },{
            name:"xing.png",
            url:"",
            link:"https://www.xing.com/profile/Johanna_Kraken/cv",
            target:"_blank"
        }];

        return { data };
    }
  }
</script>

<style lang="scss" scoped>
  .contact__linklist {
    display: grid;
    margin-top: 15px;
    grid-template-columns: repeat(3, [col-start] 1fr);
    grid-gap: 18px
  }

  ::v-deep .link > img {
    width: 250px;
  }
</style>
