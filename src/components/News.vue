<template>



  <section class="news_section">
    <div class="container">
        <div class="inner_container">

         
          <swiper
      :slidesPerView="2"
      :spaceBetween="30"
      :loop="true"
      :pagination="{
        clickable: true,
      }"
      :navigation="true"
      :modules="[Autoplay,Navigation, Pagination]"
      class="mySwiper"
      :autoplay="{
      delay: 2000,
      disableOnInteraction: false,
    }"
    >
  <!-- @swiper="onSwiper"
    
    @slideChange="onSlideChange" -->
    <swiper-slide v-for="slide in test" >
      <div class="slide_card"> 
    <div class="slide_image">
    <img :src="getImageUrl (slide.src)" alt="" srcset="" class="slide_image_class">
  </div>
      <div class="slide_textcontent">
      <div class="slide_title">
       {{ slide.title }}
      </div>
      <div class="slide_data">{{ slide.data }}</div>
    </div>
    </div>
    
    </swiper-slide>
    
    ...
  </swiper>
  <swiper :navigation="true" :modules="modules" :autoplay="2000"  class="mySwiper">
    <swiper-slide>Slide 1</swiper-slide>
    <swiper-slide>Slide 2</swiper-slide><swiper-slide>Slide 3</swiper-slide>
    <swiper-slide>Slide 4</swiper-slide><swiper-slide>Slide 5</swiper-slide>
    <swiper-slide>Slide 6</swiper-slide><swiper-slide>Slide 7</swiper-slide>
    <swiper-slide>Slide 8</swiper-slide><swiper-slide>Slide 9</swiper-slide>
  </swiper>





            <h2 class="subtitle">Новости</h2>
          
       

    
    
</div>
</div>
  </section>
  
</template>

<script setup>

import {ref,onMounted,onUnmounted } from 'vue';
import { Swiper, SwiperSlide} from 'swiper/vue';
import { Autoplay,Pagination, Navigation } from 'swiper/modules';
const modules = [Autoplay,Navigation, Pagination]

import 'swiper/css/navigation';
import 'swiper/css/pagination';
// import 'swiper/css/scrollbar';
import 'swiper/css';  
   
    const isLowScreen = ref(window.innerWidth >280 );
    const isMiddleScreen = ref(window.innerWidth < 769)
    const handleResize = () => {
        
        isLowScreen.value = window.innerWidth < 280;
        isMiddleScreen.value = window.innerWidth <769;
    };

    onMounted(() => {
      window.addEventListener('resize', handleResize);
    });

    onUnmounted(() => {
      window.removeEventListener('resize', handleResize);
    });
// import { Carousel, Navigation, Slide,Pagination } from 'vue3-carousel'

import 'vue3-carousel/dist/carousel.css'

const someObject = [
   
    
    {title:"Критерии упрощенной системы налогообложения в 2023 году",src:"../assets/pictures/thirdPage.png",data:"29 мая 2023"}
    ]
    const some1 =  [{title:"Критерии упрощенной системы налогообложения в 2023 году", src:"../assets/pictures/firstPage.png",data:"29 мая 2023"}]
    const some2 =[{title:"Критерии упрощенной системы налогообложения в 2023 году", src:"../assets/pictures/secondPage.png",data:"29 мая 2023"}]
    const slideObject = [someObject,some1,some2]

    const test = [{title:"Критерии упрощенной системы налогообложения в 2023 году",src:"../assets/pictures/thirdPage.png",data:"29 мая 2023"},{title:"Критерии упрощенной системы налогообложения в 2023 году", src:"../assets/pictures/firstPage.png",data:"29 мая 2023"},{title:"Критерии упрощенной системы налогообложения в 2023 году", src:"../assets/pictures/secondPage.png",data:"29 мая 2023"}]
    

    //carousel
    const myCarousel = ref(null)
      
     const breakpoints= {
      // 700px and up
      280: {
        itemsToShow: 1,
        snapAlign: 'center',
      },
      768: {
        itemsToShow:2,
        snapAlign: 'center',
      },
      // 1024 and up
      1024: {
        itemsToShow: 3,
        snapAlign: 'center',
      },
    }


const getImageUrl = (name) => {
      
      
      return new URL(`${name}`, import.meta.url).href;
    };

</script>

<style lang="scss" scoped>



.news_section{
  margin-top: 70px;
}
.slide_card{
  width: calc(100vw/4);
  height: auto;
  display: flex;
  flex-direction: column;
  margin: 20px;
 

  border-radius: 32px;
  background: #FFF;
  box-shadow: 0px 5px 50px 0px rgba(0, 0, 0, 0.05);
  padding-right: 20px;
}

.slide_textcontent{
  text-align: left;
}
.slide_title, .slide_data{
  padding-left: 20px;

}
.slide_title{
  color: #0A2641;

  font-size: 20px;
  
  font-weight: 600;
  line-height: 28px; 
  margin-bottom:20px;
}
.slide_data{
      color: #5F83A7;

      font-size: 16px;
      font-style: normal;
      font-weight: 600;
      line-height: 24px;
      margin-bottom:30px;
}
.slide_image_class{
  width: 100%;
  height: auto;
  @media (max-width:1000) {
    width: 250px;
    height: 280px;
    
  }
}

.navigation_buttons{
  display: flex;
  justify-content: center;
}
ol{
  padding: 0;
  
}
.button{
  display: flex;
width: 32px;
height: 32px;

border-radius: 50%;
justify-content: center;
align-items: center;
flex-shrink: 0;
background-color: #4851FD;
  position: relative;
  :hover{
    cursor: pointer;
  }
}
.prev{
  transform: rotate(180deg);
}
.carousel__icon{
    width: 1.2em;
    height: 1.2em;
    fill: var(--white);
}
</style>