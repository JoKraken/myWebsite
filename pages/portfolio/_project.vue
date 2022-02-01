<template>
  <div class="gridContainer__element">
    <h1 class="projectItem__headline">{{data.name}} <span class="projectItem__datum">{{data.datum}}</span></h1>
    <p class="projectItem__filter"> 
      <Button secoundary="true" :data="{name: data.category[0]}" @filter="filterCat"/>
      <span> | </span> 
      <Button secoundary="true" :data="{name: item}" v-for="(item, index) in data.language" :key="10+index" @filter="filterLang"/>
      <span> | </span> 
      <Button secoundary="true" :data="{name: item}" v-for="(item, index) in data.framework" :key="index" @filter="filterFram"/>
    </p>
    <p class="projectItem__describtion">{{data.desc}}</p>
    <div class="projectItem__buttons">
      <Button :data="{name: 'Github',link: data.link}" />
    </div>
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

  .projectItem__datum {
    font-size: 18px;
    color: $primary;
  }
  .projectItem__filter {
    color: $primary;
    display: inline-flex;
    flex-flow: wrap;

    span {
      padding-right: 15px;
    }
  }

  .projectItem__describtion {
    margin-bottom: 30px;
  }

  .projectItem__buttons {
    display: flex;
  }
</style>