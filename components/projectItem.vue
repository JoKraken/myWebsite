<template>
  <div class="projectItem gridContainer" v-bind:class="{ 'projectItem--right': right }">
    <div class="projectItem__img">
      <Picture v-if="data.img" :img="data.img[0]" />
    </div>
    <div class="projectItem__container">
      <h1 class="projectItem__headline">
        <span v-if="num" class="projectItem__number">{{num}}.</span>
        {{data.name}} 
        <span class="projectItem__datum">{{data.datum}}</span>
      </h1>
      <div class="projectItem__filter"> 
        <Button secoundary="true" :data="{name: data.category[0]}"/>
        <span> | </span> 
        <Button secoundary="true" :data="{name: item}" v-for="(item, index) in data.language" :key="10+index" :if="index < 2"/>
        <span> | </span> 
        <Button secoundary="true" :data="{name: item}" v-for="(item, index) in data.framework" :key="index" :if="index < 2"/>
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
        this.$emit('filter', event, 0);
      },
      filterLang(event){
        this.$emit('filter', event, 1);
      },
      filterFram(event){
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
      order: 1;
    }
    & > div:first-of-type {
      order: 2;
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

  .projectItem__img {
    text-align: center;
  }

    ::v-deep .projectItem__img > div > img {
      max-width: 90%;
    }
  
  .projectItem__headline {
    display: inline-flex;
    flex-flow: wrap;
  }

  .projectItem__number {
    font-size: 44px;
    color: $primary;
    display: inline-block;
    padding-right: 10px;
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