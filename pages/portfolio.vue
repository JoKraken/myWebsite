<template>
  <div class="gridContainer__element">
    <ProjectItems :data="projects"/>
  </div>
</template>

<script>
  export default {
    layout: 'defaultLayout',
    async asyncData({ $content, params }) {
      const projects = await $content('projects').fetch();
      return { projects }
    },
    data(){
      return {}
    }
  }
</script>
