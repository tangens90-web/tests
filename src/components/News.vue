<template>
  <section class="news_section">
    <div class="container">
        <div class="inner_container">
            <h2 class="subtitle">Новости</h2>
          
       

    
    <Carousel ref="myCarousel" :items-to-show="3" :wrap-around="true" :breakpoints="breakpoints">
    <Slide v-for="n in 3" :key="n">
    <div v-for="slide in slideObject[n] ">
      <div class="slide_card"> 
    <div class="slide_image">
    <img :src="getImageUrl (slide.src)" alt="" srcset="" class="slide_image_class"></div>
      <div class="slide_textcontent">
      <div class="slide_title">
       {{ slide.title }}
      </div>
      <div class="slide_data">{{ slide.data }}</div>
    </div>
    </div>
  </div>
    </Slide>

    <template #addons>
      <!-- <Navigation /> -->
      <div class="navigation_buttons">
      <div class="button prev" @click="myCarousel.prev()"><svg class="carousel__icon" viewBox="0 0 24 24" role="img" aria-label="Arrow pointing to the left"><title>Arrow pointing to the left</title><path d="M8.59 16.59L13.17 12 8.59 7.41 10 6l6 6-6 6-1.41-1.41z"></path></svg></div>
      <Pagination />
      <div class="button next" @click="myCarousel.next()"><svg class="carousel__icon" viewBox="0 0 24 24" role="img" aria-label="Arrow pointing to the right"><title>Arrow pointing to the right</title><path d="M8.59 16.59L13.17 12 8.59 7.41 10 6l6 6-6 6-1.41-1.41z"></path></svg></div>
    </div>
    </template>
  </Carousel>
</div>
</div>
  </section>
  
</template>

<script setup>
import{ref} from 'vue'
import { Carousel, Navigation, Slide,Pagination } from 'vue3-carousel'
import 'vue3-carousel/dist/carousel.css'

const someObject = [
   
    
    {title:"Критерии упрощенной системы налогообложения в 2023 году",src:"../assets/pictures/thirdPage.png",data:"29 мая 2023"}
    ]
    const some1 =  [{title:"Критерии упрощенной системы налогообложения в 2023 году", src:"../assets/pictures/firstPage.png",data:"29 мая 2023"}]
    const some2 =[{title:"Критерии упрощенной системы налогообложения в 2023 году", src:"../assets/pictures/secondPage.png",data:"29 мая 2023"}]
    const slideObject = {1:someObject,2:some1,3:some2}
    

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
      1368: {
        itemsToShow: 3,
        snapAlign: 'start',
      },
    }


const getImageUrl = (name) => {
      console.log(name);
      console.log(new URL(`../assets/${name}`, import.meta.url).href);
      return new URL(`${name}`, import.meta.url).href;
    };

</script>

<style lang="scss" scoped>
.news_section{
  margin-top: 70px;
}
.slide_card{
  width: 350px;
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
  font-style: normal;
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
  width: 350px;
  height: 280px;
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
// transform: rotate(90deg);
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