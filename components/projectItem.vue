<template>
  <div class="projectItem gridContainer" v-bind:class="{ 'projectItem--right': right }">
    <div class="projectItem__img">
      <img :src="'../assets/icons/code.png'" :alt="data.img">
    </div>
    <div class="projectItem__container">
      <h1 class="projectItem__headline"><span class="projectItem__number">{{num}}.</span>{{data.name}} <span class="projectItem__datum">{{data.datum}}</span></h1>
      <div class="projectItem__filter"> 
        <Button secoundary="true" :data="{name: data.category[0]}" @filter="filterCat"/>
        <span> | </span> 
        <Button secoundary="true" :data="{name: item}" v-for="(item, index) in data.language" :key="10+index" @filter="filterLang" :if="index < 2"/>
        <span> | </span> 
        <Button secoundary="true" :data="{name: item}" v-for="(item, index) in data.framework" :key="index" @filter="filterFram" :if="index < 2"/>
      </div>
      <p class="projectItem__describtion">{{data.descSmall}}</p>
      <div class="projectItem__buttons">
        <Button :data="buttonGithub" />
        <Button :data="buttonMore" />
      </div>
    </div>
  </div>
</template>

<script>
  export default {
    props: ['data', 'right', 'num'],
    data() {
      return {
        buttonGithub: {
          name: "Github",
          link: this.data.link
        },
        buttonMore: {
          name: "Mehr erfahren",
          link: "/portfolio/"+this.data.title,
          sameTap: true
        }
      };
    },
    methods: {
      filterCat(event){
        console.log(event);
        this.$emit('filter', event, 0);
      },
      filterLang(event){
        console.log(event);
        this.$emit('filter', event, 1);
      },
      filterFram(event){
        console.log(event);
        this.$emit('filter', event, 2);
      }
    }
  }
</script>
             
<style lang="scss" scoped>
  .projectItem {
    border: $primary 1px solid;
    border-radius: 10px;
    margin-bottom: 30px;
  }

  .projectItem--right {
    & > div {
      grid-column: col-start 1;
    }
    & > div:first-of-type {
      grid-column: col-start 7;
    }

    .projectItem__container {
      padding-left: 30px;
      padding-right: 0;

      @include for-phone {
        padding-right: 30px;
      }
    }
  }

  .projectItem > div {
    grid-column: span 6;

    @include for-phone {
      grid-column: span 12;
    }
  }

  .projectItem__container {
    padding-bottom: 30px;
    padding-right: 30px;

    @include for-phone {
      padding-left: 30px;
    }
  }
  
    .projectItem__headline {
      display: inline-flex;
      flex-flow: wrap;
    }

  .projectItem__number {
    font-size: 44px;
    color: $primary;
    display: inline-block;
  }

  .projectItem__datum {
    font-size: 18px;
    color: $primary;
  }

  .projectItem__filter {
    display: flex;
    color: $primary;
    display: inline-flex;
    flex-flow: wrap;

    span {
      padding-right: 15px;
    }
  }

  .projectItem__describtion {
    margin-bottom: 30px;
    overflow: hidden;
    display: -webkit-box;
    -webkit-box-orient: vertical;
    -webkit-line-clamp: 3;
  }

  .projectItem__buttons {
    display: flex;
  }
</style>