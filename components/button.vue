<template>
  <a class="button" :href="data.link" target="_blank">
    {{data.name}}
  </a>
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