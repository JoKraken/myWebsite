<template>
  <div class="projectItems">
    <h1>Hier sind meine Projekte:</h1>
    <ProjectItem v-for="(project, index) in data" :key="index" :data="project" :right="index%2==1"/>
  </div>
</template>

<script>
  export default {
      props: ['data'],
      data() {
          return {};
      }
  }
</script>
             
<style lang="scss" scoped>

</style>