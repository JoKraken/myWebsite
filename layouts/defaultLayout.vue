<template>
  <div lang="en" class="container gridContainer">
    <Header />
    
    <Nuxt class="content"/>
    
    <Footer />
  </div>
</template>

<style lang="scss" scoped>
.content {
    @media (max-width: 767px) {
        padding: 0 12px;
    }
}
</style>