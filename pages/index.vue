<template>
  <div class="gridContainer__element">
    <div class="introduction">
      <p>Hey there!</p>
      <p>
        <span> I'm a web developer. Have a look at my </span>
        <a href="/portfolio/" class="introduction__link">projects</a>
        <span> and contact me.</span>
        </p>
      <p>I have some expierience with frontend programming. If you want to look at it, here are a few exsamples:</p>
    </div>
    <ProjectItem v-for="(project, index) in projects" :key="index" :data="project" :right="index%2==1"/>
  </div>
</template>

<script>
  export default {
    layout: 'defaultLayout',
    data(){
      return {}
    },
    async asyncData({ $content, params }) {
      const projects = [];
      let temp = await $content('projects', 'login').fetch();
      projects.push(temp);
      temp = await $content('projects', 'slackbot').fetch();
      projects.push(temp);
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

  .introduction__link {
    color: $primary;
  }
</style>