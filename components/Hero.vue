<template>
  <div class="max-w-md sm:max-w-xl lg:max-w-6xl mx-auto pt-4 carousel-cont">
    <carousel >
      <carousel-slide v-for="slide in slides" :key="slide" class="carousel-slider">
        <img :src="slide" :alt="slide">
      </carousel-slide>
    </carousel>
    <!-- <div class="px-8 py-12 max-w-md mx-auto sm:max-w-xl lg:max-w-full lg:w-1/2 lg:py-24 lg:px-12"> -->
      <!-- <Slider/> -->
    <!-- </div> -->
  </div>
</template>

<script>
import Slider from './Slider.vue';
import Carousel from './carousel/Carousel.vue';
import CarouselSlide from './carousel/CarouselSlide.vue';
export default {
  name: 'hero',
  components: {
    Slider,
    Carousel: Carousel,
    CarouselSlide: CarouselSlide,
  },
  data(){
    return{
      slides: [
        'https://picsum.photos/id/230/600/300',
        'https://picsum.photos/id/231/600/300',
        'https://picsum.photos/id/232/600/300',
        'https://picsum.photos/id/233/600/300',
        'https://picsum.photos/id/234/600/300',
        'https://picsum.photos/id/235/600/300',
        'https://picsum.photos/id/236/600/300',
      ]
    }
  }
}
</script>

<style>
  .carousel-cont {
    display:flex;
    justify-content: center;
  }
  .carousel {
    position:relative;
    overflow: hidden;
    /* width:800px; */
    width: 1151px;
    height:500px;
    z-index:10;
  }
  .btns {
    padding:5px 10px;
    background-color:rgba(0,0,0,0.5);
    border:1px solid transparent;
    margin:5px 10px;
    color:#FFF;
    height:50px;
    width:50px;
    position:absolute;
    margin-top:-25px;
    z-index:2;
  }
  .btns:hover {
    cursor: pointer;
  }
  .btns:focus{
    outline:none;
  }
  .btns-next {
    top:50%;
    right:0;
  }
  .btns-prev {
    top:50%;
    left:0;
  }
  .carousel-slider {
    position:absolute;
    top:0;
    left:0;
    bottom:0;
    right:0;
  }
  .carousel-slider img {
    width:100%;
    height:100%;
  }
</style>