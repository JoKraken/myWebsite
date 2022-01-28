<template>
  <div class="gridContainer__element">
    <div class="introduction">
      <p>Hey there!</p>
      <p>I'm a web developer. Have a look at my <Links class="introduction__links" :data="data"/> and contact me.</p>
      <p>I have some expierience with frontend programming. If you want to look at it, here are a few exsamples:</p>
    </div>
    <ProjectItem v-for="(project, index) in projects" :key="index" :data="project" :right="index%2==1"/>
  </div>
</template>

<script>
  export default {
    layout: 'defaultLayout',
    data(){
      return {
        data: {
          link: "/portfolio",
          url: "projects"
        }
      }
    },
    async asyncData({ $content, params }) {
      const projects = [];
      let temp = await $content('projects', 'login').fetch();
      projects.push(temp);
      temp = await $content('projects', 'slackbot').fetch();
      projects.push(temp);
      console.log(projects);
      return { projects }
    },
  }
</script>

<style lang="scss" scoped>
  .introduction {
    p {
      font-size: 50px;
    }
  }

  .introduction__links {
    color: $primary;
  }
</style>