<template>
    <header>    
        <div class="header_inner">
            <HeaderModal v-if="consultationButton" @closeHeaderModal="closeHeaderModal"></HeaderModal>
            <div class="container">
                <div class="inner_container">
                    <div class="flex_container">
                        
                    <div class="left_block">
                        
                    <div class="logo_block">
                        <div class="logo blue"></div>
                        <div class="logo orange"></div>

                        
                    </div>
                    <div class="logo_text">pascal</div>
                    <nav>
                        <div class="menu_items" v-if="isMiddleScreen" @click="menuList=!menuList"><div class="menu_title">Меню
                            
                        </div>
                            <div class="menu_svg">
                            <svg class="carousel__icon" viewBox="0 0 24 24" role="img" aria-label="Arrow pointing to the left"><title>Arrow pointing to the left</title><path d="M8.59 16.59L13.17 12 8.59 7.41 10 6l6 6-6 6-1.41-1.41z"></path></svg>
                        
                        </div>
                        <div class="menu_list" v-if="menuList"> 

                        <li class="menu_item">Преимущества</li>
                        <li class="menu_item">Услуги</li>
                        <li class="menu_item">Новости</li>
                        <li class="menu_item">Отзывы</li>
                        </div>
                    </div>
                        <ul class="nav_list" v-if="isHighScreen">

                            <li class="nav_item">Преимущества</li>
                            <li class="nav_item">Услуги</li>
                            <li class="nav_item">Новости</li>
                            <li class="nav_item">Отзывы</li>
                        </ul>
                        
                    </nav>
                </div>
                <div class="right_block">
                    <div class="number">
                        8 (812) 603-71-79
                    </div>
                    <div class="button">
                        <button class="button_call">
                            Обратный звонок
                        </button>
                    </div>

                </div>
                <button class="burger_btn" @click="toggle" v-if="isLowScreen"><span></span></button>
            </div>
            <div class="accounting_service">
                <div class="accounting_service_title">
                
                <h3>Бухгалтерские услуги <br>в Санкт-Петербурге</h3>
            </div>
            <div class="accounting_service_text">
                
                Наши специалисты дадут исчерпывающую <br> информацию по интересующим вас услугам
            </div>
            <div class="accounting_service_button">
                
                <button class="button_consultation" @click="consultationButton=true"> Получить бесплатную консультацию</button>
                
            </div>
            </div>
            </div>
        </div>
    </div>

    </header>
   
    <Addvantages/>
    <Pricelist/>
    <News/>
    <Askmodal/>
     <Footeritems/>
</template>

<script setup>
import Addvantages from './Addvantages.vue';
import Pricelist from './Pricelist.vue';
import News from './News.vue';
import Askmodal from './Askmodal.vue';
import Footeritems from './Footeritems.vue';
import HeaderModal from './HeaderModal.vue'

import {ref,onMounted,onUnmounted } from 'vue';
    const consultationButton = ref(false)
    const serviceItems =  ref([])
    const toggleService = (index)=>{
        console.log(serviceItems.value[index],index);
        serviceItems.value[index].classList.toggle("active")
        
    }
    const menuList = ref(false)


    
    const isLowScreen = ref(window.innerWidth <420)
    const isHighScreen = ref(window.innerWidth >1000);
    const isMiddleScreen = ref( window.innerWidth>=420&& window.innerWidth < 1000  )
    const handleResize = () => {
        isLowScreen.value = window.innerWidth <420
        isHighScreen.value = window.innerWidth> 1000;
        isMiddleScreen.value = window.innerWidth>=420 && window.innerWidth < 1000 ;
    };

    onMounted(() => {
      window.addEventListener('resize', handleResize);
    });

    onUnmounted(() => {
      window.removeEventListener('resize', handleResize);
    });
    

const closeHeaderModal = (bool)=>{
    console.log("eqeqeq");
    consultationButton.value = bool
    console.log(consultationButton);
}





</script>

<style lang="scss" scoped>
    
    @import url('../static/burgerbutton.scss');


    .header_inner{
        width: 100%;
        max-width: 100vw;
        height: auto;
        background-color: var(--blue);
        color: var(--white);
        padding-top: 50px;
        position: relative;
    }
    .flex_container{
        display: flex;
        justify-content: space-between;
        position: relative;
    }
    .left_block{
        display: flex;
        justify-content: left;
        
    }
    //menu
    .menu_items{
        display: flex;
        justify-content: left;
        padding-left: 20px;
        cursor: pointer;
    }
    .menu_svg{
        color:#FF6A2A;
        transform: rotate(90deg);
    }
    .menu_list{
        position: absolute;
        width: 120px;
        background-color: white;
        top: 20px;
    }
    .menu_item{
        color: black;
        font-size: 16px;
        list-style-type: none;
    }
    .logo_block{
        position: relative;
        width: 40px;
    }
    .logo{
        width: 23px;
        height: 22px;
        border-radius: 50%;
        position: absolute;
        top: 0;
         
    }
    .blue{
            background-color: #4851FD;
            z-index: 10;
        }
    .orange{
        background-color: #FF6A2A;
        z-index:15;
        left:12px;
        }
    .logo_text{
        color: var(--white);

        font-size: 24px;
        font-style: normal;
        font-weight: 600;
        line-height: normal;
    }   
    .nav_list{
        display: flex;
        justify-content: left;
    }
    .nav_item{
        list-style-type: none;
        opacity:0.5;
        color: var(--white);

        font-size: 15px;
        font-style: normal;
        font-weight: 600;
        line-height: 28px; 
        margin-right: 20px;

    } 


    //right
    .right_block{
        display: flex;
        padding-right: 30px;
        
    }
    .number{
        color: var(--white);
        
        font-size: 18px;
        font-style: normal;
        font-weight: 600;
        line-height: 28px;
        margin-right: 10px; 
        @media (max-width:420px) {
            font-size: 13px;
            


}
    }
    .button_call{
        
        width: 172px;
        height: 44px;
        padding: 10px 24px;
        margin-top: -5px;
        border-radius: 32px;
        background: rgba(255, 255, 255, 0.15);
        color: var(--white);
        @media (max-width:600px) {
            display: none;
        }

    }


    //accounting_services
    .accounting_service{
        margin-top: 35px;
    }
    .accounting_service_title{
        color: var(--white);
        
        font-size: 56px;
        font-style: normal;
        font-weight: 700;
        line-height: 72px; 
        @media (max-width: 420px) {
            font-size:36px;
            
        }
    }
    .accounting_service_text{

        color: var(--white);
        margin: 35px 0;
        
        font-size: 18px;
        font-style: normal;
        font-weight: 600;
        line-height: 28px; 
        opacity: 0.5;
        @media (max-width: 420px) {
            font-size:14px;
            
        }
    }
    .button_consultation{
        padding: 18px 32px;
        border-radius: 32px 0px;
        background: linear-gradient(169deg, #4851FD 0%, #FF6A2A 100%), #4851FD;
        color: var(--white);
        font-size: 18px;
        font-style: normal;
        font-weight: 600;
        line-height: 24px;  
        @media (max-width: 420px) {
            font-size:14px;
            
        }
    }
    .accounting_service_button{
        padding-bottom: 70px;
    }




</style>

