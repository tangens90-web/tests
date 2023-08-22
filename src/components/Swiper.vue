<template>
  <div class="container">
    <swiper
      :slidesPerView="2"
      :spaceBetween="30"
      :loop="true"
      :breakpoints="breakpoints"
      :pagination="{
        clickable: true,
      }"
      :navigation="true"
      :modules="modules"
      class="mySwiper"
      
    >
   
    <swiper-slide v-for="slide in test" >
      <div class="some">
      <!-- <a href=""> -->
     

      <div class="slide_image">
    <img :src="getImageUrl (slide.src)" alt="" srcset="" class="slide_image_class">
  </div>
  <div>{{ slide.title }}</div>
  <div class="slide_data">{{ slide.data }}</div>
<!-- </a> -->
</div>


    
    </swiper-slide>
    <Navigation/>
      
    </swiper>
    
  </div>
  
  </template>
  <script >
    // Import Swiper Vue.js components
    import { Swiper, SwiperSlide } from 'swiper/vue';
  
    // Import Swiper styles
    import 'swiper/css';
    // import 'swiper/css/autoplay';
    import 'swiper/css/pagination';
    import 'swiper/css/navigation';
  
    // import './style.css';
  
    // import required modules
    import { Autoplay,Pagination, Navigation } from 'swiper/modules';
  
    export default {
      components: {
        Swiper,
        SwiperSlide,
        
      },
      setup() {
        const test = [{title:"Критерии упрощенной системы налогообложения в 2023 году",src:"../assets/pictures/thirdPage.png",data:"29 мая 2023"},{title:"Критерии упрощенной системы налогообложения в 2023 году", src:"../assets/pictures/firstPage.png",data:"29 мая 2023"},{title:"Критерии упрощенной системы налогообложения в 2023 году", src:"../assets/pictures/secondPage.png",data:"29 мая 2023"},{title:"Критерии упрощенной системы налогообложения в 2023 году",src:"../assets/pictures/thirdPage.png",data:"29 мая 2023"},
        {title:"Критерии упрощенной системы налогообложения в 2023 году",src:"../assets/pictures/thirdPage.png",data:"29 мая 2023"},{title:"Критерии упрощенной системы налогообложения в 2023 году", src:"../assets/pictures/firstPage.png",data:"29 мая 2023"},{title:"Критерии упрощенной системы налогообложения в 2023 году", src:"../assets/pictures/secondPage.png",data:"29 мая 2023"},{title:"Критерии упрощенной системы налогообложения в 2023 году",src:"../assets/pictures/thirdPage.png",data:"29 мая 2023"},]
        const getImageUrl = (name) => {
      
      
      return new URL(`${name}`, import.meta.url).href;
    };
    const breakpoints= {
      // 700px and up
      280: {
        slidesPerView: 1,
        spaceBetween: 10,
      },
      768: {
        slidesPerView:2,
        spaceBetween: 20
      },
      // 1024 and up
      1368: {
        slidesPerView: 3,
        spaceBetween: 30.
      },
    }
        return {
            test,
            getImageUrl,
            breakpoints,
          modules: [Autoplay,Pagination, Navigation],
        };
      },
    };
  </script>
  <style lang="scss" scoped>
 //change .swiper_pagination: position relative!! it's absolute now

.swiper {
  width: 100%;
  height: 100%;
  
}

.some{
  display: flex;
  flex-direction: column;
 
  
}
.swiper-slide {
  text-align: center;
  font-size: 18px;
  background: #fff;

  /* Center slide text vertically */
  display: flex;
  justify-content: center;
  align-items: center;
}

.swiper-slide img {
  display: block;
  width: 100%;
  height: 100%;
  object-fit: cover;
}



          
      
    
  </style>