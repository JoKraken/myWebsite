<template>
  <div class="gridContainer__element">
    <h1>Ich bin unter folgenden Social-Media-Acounts erreichen:</h1> 
    <div class="contact__linklist">
      <!--Links v-for="(item, index) in data" :key="index" :type="svg" :data="item"/-->
      <svg :xmlns="img" >
    <title
      :id="iconName"
      lang="en"
    >{{ iconName }} icon</title>
    <g :fill="iconColor">
      <slot />
    </g>
  </svg>
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

        return { data };
    }
  }
</script>

<style lang="scss" scoped>
  .contact__linklist {
    display: grid;
  }
</style>
