<template>
    <select class="filters" :name="art" :id="art" @change="filter()" v-model="selected">
        <option value="none" selected>{{defaultItem}}</option>
        <option class="filters__option" v-for="(item, index) in options" :key="index" :value="item">{{item}}</option>
    </select>
</template>

<script>
  export default {
    props: ['options', 'defaultItem', 'art'],
    data() {
        let selected = "none";

        return { selected };
    },
    methods: {
        filter(){
            this.$emit('filter', this.selected);
        },
        editSelected(op){
            this.selected = op;
        }
    }
  }
</script>
             
<style lang="scss" scoped>
    .filters {
        margin-top: 15px;
        min-width: 150px;
        border: $primary 1px solid;
        border-radius: 5px;
        padding: 10px;
    }

    ::v-deep option:hover{
        background-color: $primary;
    }
</style>