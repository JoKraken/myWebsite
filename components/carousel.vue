<template>
    <div id="slider">
      <transition-group tag="div" :name="transitionName" class="slides-group">
        <div v-if="show" :key="current" class="slide">
          <Picture class="carousel__img" :img="getURL()" />
          <p></p>
        </div>
      </transition-group>
      <div v-if="imgs.length" class="btn btn-prev" aria-label="Previous slide" @click="slide(-1)">
        &#10094;
      </div>
      <div v-if="imgs.length" class="btn btn-next" aria-label="Next slide" @click="slide(1)">
        &#10095;
      </div>
    </div> 
</template>

<script>
export default {
  props: ['imgs'],
  data(){
      return {
        current: 0,
        direction: 1,
        transitionName: "fade",
        show: false,
    }
  },
  methods: {
    getURL(){
      return this.imgs[this.current];
    },
    slide(dir) {
      this.direction = dir;
      dir === 1
        ? (this.transitionName = "slide-next")
        : (this.transitionName = "slide-prev");
      var len = this.imgs.length;
      this.current = (this.current + dir % len + len) % len;
    }
  },
  mounted() {
    this.show = true;
  }
}
</script>

<style lang="scss" scoped>

/* FADE IN */
.fade-enter-active {
  transition: opacity 1s;
}
.fade-enter {
  opacity: 0;
}

/* GO TO NEXT SLIDE */
.slide-next-enter-active,
.slide-next-leave-active {
  transition: transform 0.5s ease-in-out;
}
.slide-next-enter {
  transform: translate(100%);
}
.slide-next-leave-to {
  transform: translate(-100%);
}

/* GO TO PREVIOUS SLIDE */
.slide-prev-enter-active,
.slide-prev-leave-active {
  transition: transform 0.5s ease-in-out;
}
.slide-prev-enter {
  transform: translate(-100%);
}
.slide-prev-leave-to {
  transform: translate(100%);
}

/* SLIDER STYLES */

.carousel__img,
#slider {
  position: relative;
}

.slides-group {
  width: 90%;
  position: relative;
  margin: auto;
}

#slider {
  overflow: hidden;
  border: $primary 1px solid;
  border-radius: 10px;
}

.slide {
  width: 100%;
  position: absolute;
  top: 0;
  left: 0;
  right: 0;
  display: flex;
  align-items: center;
  justify-content: center;
}

.btn {
  z-index: 10;
  cursor: pointer;
  display: flex;
  justify-content: center;
  align-items: center;
  width: 50px;
  height: 50px;
  position: absolute;
  top: calc(50% - 35px);
  left: 1%;
  transition: transform 0.3s ease-in-out;
  user-select: none;
  color: $primary;
      font-size: 54px;
}

.btn-next {
  left: auto;
  right: 1%;
}

.btn:hover {
  transform: scale(1.1);
}
</style>
