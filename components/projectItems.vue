<template>
  <div class="projectItems">
    <h1 class="projectItems__headline">Meine Projekte</h1>
    <div class="projectItems__filter">
      <label>Filter:</label> 
      <Filters v-bind:options="categories" art="categories" defaultItem="Alle Arten" @filter="filterAfterProject" ref="formArt" />
      <Filters v-bind:options="languages" art="languages" defaultItem="Alle Sprachen" @filter="filterAfterLanguage" ref="formLang" />
      <Filters v-bind:options="frameworks" art="frameworks" defaultItem="Alle Frameworks" @filter="filterAfterFramework" ref="formFram" />
      <Button class="projectItems__filter-button" :data="revers" @filter="reset" />
    </div>
    <div class="projectItems__itemsCount">( {{projects.length}} )</div>
    <ProjectItem v-for="(project, index) in projects" :key="index" :num="index+1" :data="project" :right="index%2==1" @filter="filter"/>
    <div v-if="projects.length == 0">Es wurden keine Projekte mit den Filtereinstellungen gefunden</div>
  </div>
</template>

<script>
  export default {
    props: ['data'],
    data() {
      let projects = this.data;
      let languages = [];
      let frameworks = [];
      let categories = [];
      let filterOp = ["none", "none", "none"];
      let revers = {name: "Filter löschen"};

      return { projects, categories, languages, frameworks, revers, filterOp };
    },
    created() {
      this.getFilters();
    },
    methods: {
      reset(){
        this.filterOp = ["none", "none", "none"];
        this.projects = this.data;
        this.$refs.formArt.editSelected("none");
        this.$refs.formFram.editSelected("none");
        this.$refs.formLang.editSelected("none");
      },
      getFilters(){
          this.data.forEach(element => {
            let isIn = false;
            element.language.forEach(ellang => {
              this.languages.forEach(language => {
                if(language == ellang) isIn = true;
              });
              if(!isIn) this.languages.push(ellang);
              isIn = false;
            });
            element.framework.forEach(elfram => {
              if(elfram != '')
                this.frameworks.forEach(framework => {
                  console.log(framework);
                  if(framework == elfram) isIn = true;
                });
              if(!isIn) this.frameworks.push(elfram);
              isIn = false;
            });
            element.category.forEach(elcate => {
              this.categories.forEach(category => {
                if(category == elcate) isIn = true;
              });
              if(!isIn) this.categories.push(elcate);
              isIn = false;
            });
          });
      },
      filterAfterProject(event){
        this.filterOp[0] = event;
        this.filterOptions();
        this.$refs.formArt.editSelected(event);
      }, 
      filterAfterLanguage(event){
        this.filterOp[1] = event;
        this.filterOptions();
        this.$refs.formLang.editSelected(event);
      },
      filterAfterFramework(event){
        this.filterOp[2] = event;
        this.filterOptions();
        this.$refs.formFram.editSelected(event);
      },
      filter(event, count) {
        if(count == 0)
          this.filterAfterProject(event);
        else if(count == 1)
          this.filterAfterLanguage(event);
        else if(count == 2)
          this.filterAfterFramework(event);
      },
      filterOptions() {
        let temp = [];
        let isIn = false;
        this.data.forEach(item => {
          item.category.forEach(itemCat => {
            if(this.filterOp[0] == "none") isIn = true;
            else if(itemCat == this.filterOp[0]) isIn = true;
          });
          if(isIn) temp.push(item);
          isIn = false;
        });
        let temp2 = [];
        temp.forEach(item => {
          item.language.forEach(itemLang => {
            if(this.filterOp[1] == "none") isIn = true;
            else if(itemLang == this.filterOp[1]) isIn = true;
          });
          if(isIn) temp2.push(item);
          isIn = false;
        });
        let temp3 = [];
        temp2.forEach(item => {
          item.framework.forEach(itemFram => {
            if(this.filterOp[2] == "none") isIn = true;
            else if(itemFram == this.filterOp[2]) isIn = true;
          });
          if(isIn) temp3.push(item);
          isIn = false;
        });
        this.projects = temp3;
      }
    }
  }
</script>
             
<style lang="scss" scoped>
  .projectItems__headline,
  .projectItems__filter {
    margin-bottom: 20px;

    @include for-phone {
      margin-bottom: 10px;
    }
  }

  .projectItems__filter {
    text-align: right;
    width: 100%;

    @include for-phone {
      text-align: left;
    }
  }

  .projectItems__filter-button {
    display: inline-flex;
    margin-top: 15px;
    margin-left: 15px;
    text-align: right;

    @include for-phone {
      margin-left: 0;
    }
  }

  .projectItems__itemsCount {
    color: $primary;
    text-align: right;
    width: 100%;
    margin-bottom: 30px;

    @include for-phone {
      margin-bottom: 20px;
    }
  }
</style>