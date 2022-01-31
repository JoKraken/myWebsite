<template>
  <div class="projectItems">
    <h1 class="projectItems__headline">Hier sind meine Projekte:</h1>
    <div class="projectItems__filter">
      <label for="language">Filter:</label>
      <select name="language" id="language">
        <option v-for="(language, index) in languages" :key="index" :value="language">{{language}}</option>
      </select>
    </div>
    <ProjectItem v-for="(project, index) in data" :key="index" :data="project" :right="index%2==1"/>
  </div>
</template>

<script>
  export default {
    props: ['data'],
    data() {
      let languages = [];

      this.data.forEach(element => {
        
      });
      return {languages};
    }
  }
</script>
             
<style lang="scss" scoped>
  .projectItems__headline {
    margin-bottom: 50px;

    @include for-phone {
      margin-bottom: 30px;
    }
  }
</style>