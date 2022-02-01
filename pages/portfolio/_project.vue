<template>
  <div class="gridContainer__element">
    <Links :data="{link: '/portfolio/', name: 'left-arrow', url: 'zurück'}"/>
    <h1 class="project__headline">{{data.name}} <span class="project__datum">{{data.datum}}</span></h1>
    <p class="project__filter"> 
      <Button secoundary="true" :data="{name: data.category[0]}"/>
      <span> | </span> 
      <Button secoundary="true" :data="{name: item}" v-for="(item, index) in data.language" :key="10+index"/>
      <span> | </span> 
      <Button secoundary="true" :data="{name: item}" v-for="(item, index) in data.framework" :key="index"/>
    </p>
    <p class="project__describtion">{{data.desc}}</p>
    <div class="project__buttons">
      <Button :data="{name: 'Github',link: data.link}" />
    </div>

    <Carousel class="project__carousel" :imgs="data.img"/>
  </div>
</template>

<script>
  export default {
    layout: 'defaultLayout',
    async asyncData({ $content, params }) {
      const data = await $content('projects', params.project).fetch();
      return { data }
    },
    data(){
      return {}
    }
  }
</script>

<style lang="scss" scoped>

  .project__datum {
    font-size: 18px;
    color: $primary;
  }
  .project__filter {
    color: $primary;
    display: inline-flex;
    flex-flow: wrap;

    span {
      padding-right: 15px;
    }
  }

  .project__describtion {
    margin-bottom: 30px;
  }

  .project__buttons {
    display: flex;
  }

  ::v-deep .project__carousel {
    margin: 30px 0;
    height: 40vh;

   .carousel__img {
      height: 40vh;
    }
  }
</style>