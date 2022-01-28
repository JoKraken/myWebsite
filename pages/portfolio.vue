<template>
  <div class="gridContainer__element">
    <ProjectItems :data="projects"/>
  </div>
</template>

<script>
  export default {
    layout: 'defaultLayout',
    async asyncData({ $content, params }) {
      const projects = await $content('projects').fetch()
      console.log(projects);
      return { projects }
    },
    data(){
      return {
        projects: [{
          name: "test",
          datum: "2021",
          desc:"lorum ipsum",
          img: "",
          link: "https://www.google.com/",
        },{
          name: "test2",
          datum: "2021",
          desc:"lorum ipsum",
          img: "",
          link: "https://www.google.com/",
          right: true
        }]
      }
    }
  }
</script>
