<template>
  <div class="projectItem gridContainer" v-bind:class="{ 'projectItem--right': right }">
    <div class="projectItem__img">
      <img src="" alt="">
    </div>
    <div class="projectItem__container">
      <h1 class="projectItem__headline">{{data.name}} <span class="projectItem__datum">{{data.datum}}</span></h1>
      <p>{{data.desc}}</p>
      <Button :data="button" />
    </div>
  </div>
</template>

<script>
  export default {
      props: ['data', 'right'],
      data() {
          return {button: {
            name: "Github",
            link: this.data.link
          }};
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
    & > div:first-of-type {
      grid-column: col-start 7 / span 6;
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

  .projectItem__datum {
    font-size: 18px;
    color: $primary;
  }
</style>