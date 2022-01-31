<template>
  <div v-if="data" :class="secoundary ? 'secoundary' : ''">
    <a v-if="data.link != undefined" class="button" :href="data.link" target="_blank">
      {{data.name}}
    </a>
    <a v-if="data.link == undefined" class="button" @click="filter()">
      {{data.name}}
    </a>
  </div>
</template>

<script>
  export default {
    props: ['data', 'secoundary'],
    data() {
        return {};
    },
    methods: {
      filter(){
          this.$emit('filter', this.data.name);
      }
    }
  }
</script>
             
<style lang="scss" scoped>
  .secoundary {
      .button {
        border: none;
        color: $primary;
        background-color: transparent;
        padding: 0 15px 0 0;
      }
  }

  .button {
      background-color: $primary;
      border: $primary 1px solid;
      border-radius: 5px;
      color: $white;
      padding: 10px;
      text-decoration: none;

      &:hover {
          text-decoration: underline;
      }
  }
</style>