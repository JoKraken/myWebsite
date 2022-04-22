<template>
  <div lang="en" class="container gridContainer">
    <Header />
    
    <Nuxt class="content"/>
    
    <Footer />
  </div>
</template>

<style lang="scss" scoped>
.content {
    min-height: 59vh; 

    @include for-phone {
        min-height: 53vh;
        padding: 0 12px;
    }
}
</style>