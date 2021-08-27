<template>
  <div class="app-container">
    <aside>
      The guide page is useful for some people who entered the project for the first time. You can briefly introduce the
      features of the project. Demo is based on
      <a href="https://github.com/kamranahmedse/driver.js" target="_blank">driver.js.</a>
    </aside>
    <el-button icon="el-icon-question" type="primary" @click.prevent.stop="guide">
      Show Guide
    </el-button>

    <slick
      ref="slick"
      :options="slickOptions"
      @afterChange="handleAfterChange"
      @beforeChange="handleBeforeChange"
      @breakpoint="handleBreakpoint"
      @destroy="handleDestroy"
      @edge="handleEdge"
      @init="handleInit"
      @reInit="handleReInit"
      @setPosition="handleSetPosition"
      @swipe="handleSwipe"
      @lazyLoaded="handleLazyLoaded"
      @lazyLoadError="handleLazeLoadError">
      <a href="http://placehold.it/200x100"><img src="http://placehold.it/200x100" alt="">
        txt-1
      </a>
      <a href="http://placehold.it/200x100"><img src="http://placehold.it/200x100" alt="">
        txt-2
      </a>
      <a href="http://placehold.it/200x100"><img src="http://placehold.it/200x100" alt="">
        txt-3
      </a>
      <a href="http://placehold.it/200x100"><img src="http://placehold.it/200x100" alt="">
        txt-4
      </a>
      <a href="http://placehold.it/200x100"><img src="http://placehold.it/200x100" alt="">
        txt-5
      </a>
    </slick>

  </div>
</template>

<script>
import Driver from 'driver.js' // import driver.js
import 'driver.js/dist/driver.min.css' // import driver.js css
import steps from './steps'
import Slick from 'vue-slick'
import 'slick-carousel/slick/slick.css';

export default {
  name: 'Guide',
  components: { Slick },
  data() {
    return {
      slickOptions: {
        slidesToShow: 3,
        slidesToScroll: 3
      },
      driver: null
    }
  },
  mounted() {
    this.driver = new Driver()
  },
  methods: {
    guide() {
      this.driver.defineSteps(steps)
      this.driver.start()
    },
    next() {
      this.$refs.slick.next();
    },

    prev() {
      this.$refs.slick.prev();
    },

    reInit() {
      // Helpful if you have to deal with v-for to update dynamic lists
      this.$nextTick(() => {
        this.$refs.slick.reSlick();
      });
    },

    // Events listeners
    handleAfterChange(event, slick, currentSlide) {
      console.log('handleAfterChange', event, slick, currentSlide); 
    },
    handleBeforeChange(event, slick, currentSlide, nextSlide) {
      console.log('handleBeforeChange', event, slick, currentSlide, nextSlide);
    },
    handleBreakpoint(event, slick, breakpoint) {
      console.log('handleBreakpoint', event, slick, breakpoint);
    },
    handleDestroy(event, slick) {
      console.log('handleDestroy', event, slick);
    },
    handleEdge(event, slick, direction) {
      console.log('handleEdge', event, slick, direction);
    },
    handleInit(event, slick) {
      console.log('handleInit', event, slick);
    },
    handleReInit(event, slick) {
      console.log('handleReInit', event, slick);
    },
    handleSetPosition(event, slick) {
      console.log('handleSetPosition', event, slick);
    },
    handleSwipe(event, slick, direction) {
      console.log('handleSwipe', event, slick, direction);
    },
    handleLazyLoaded(event, slick, image, imageSource) {
      console.log('handleLazyLoaded', event, slick, image, imageSource);  
    },
    handleLazeLoadError(event, slick, image, imageSource) {
      console.log('handleLazeLoadError', event, slick, image, imageSource);
    },
  }
}
</script>