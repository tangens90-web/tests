<template>
    <section class="price_list">
    <div class="container">
        <div class="inner_container">
            <h2 class="addvantages subtitle">Прайс-лист на бухгалтерские услуги</h2>
            <div class="price_description">
                <h3 class="price_description_title">В стоимость ежемесячного бухгалтерского обслуживания входит</h3>
                <div class="price_items">
                <div class="price_item" v-for="item in priceItems" :key="item">
                    <div class="price_item_svg">
                        <svg xmlns="http://www.w3.org/2000/svg" width="20" height="20" viewBox="0 0 20 20" fill="none">
  <g clip-path="url(#clip0_1_337)">
    <path d="M18.3333 9.23818V10.0049C18.3323 11.8019 17.7504 13.5504 16.6744 14.9897C15.5984 16.429 14.086 17.4819 12.3628 17.9914C10.6395 18.501 8.79768 18.4398 7.11202 17.817C5.42636 17.1942 3.98717 16.0433 3.00909 14.5357C2.03101 13.0282 1.56645 11.2449 1.68469 9.45178C1.80293 7.65866 2.49763 5.95179 3.66519 4.58575C4.83275 3.2197 6.41061 2.26767 8.16345 1.87164C9.91629 1.47561 11.7502 1.6568 13.3916 2.38818M18.3333 3.33341L9.99996 11.6751L7.49996 9.17508" stroke="#4851FD" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"/>
  </g>
  <defs>
    <clipPath id="clip0_1_337">
      <rect width="20" height="20" fill="white"/>
    </clipPath>
  </defs>
</svg>
                    </div>
                    <div class="price_item_title">
                        {{ item.title }}
                    </div>

                </div>

            </div>

            </div>


            <div class="service_description">
                <div class="c" v-if="true">
                    <div class="service_item " v-for="item in tabletitles"
                >
                   
                    <div class="service_item_title blue"
                    v-if="!isLowScreen">
                       {{item.title}}
                    </div>
                    <div class="service_item_prices">

                    <div class="service_item_price">
                        <div v-if="!isLowScreen" class="lowScreen">
                            <div>{{item.osn}}</div>
                            </div>
                            
                        
                    </div>
                    
                    <div class="service_item_price">
                        <div v-if="!isLowScreen" class="lowScreen">
                            <div>{{item.usn15}}</div>
                            
                    </div>
                </div>
                    <div class="service_item_price">
                        <div v-if="!isLowScreen" class="lowScreen">
                            <div>{{item.usn6}}</div>
                            </div>
                            
                    </div>
                
            </div>

                </div>
                 
                

                
                <div class="service_item" 
                v-for="item,index in servicesPrices" :key="item" >
                   
                    <div class="service_item_title">
                        {{ item.title }}
                    </div>
                    <div class="service_item_prices" :ref="(el) =>serviceItems[index] = el">

                    <div class="service_item_price">
                        <div v-if="isLowScreen" class="lowScreen">
                            <div>ОСН</div>
                            <div>
                            {{ item.osn}}
                            <sup class="price_reg" v-if="checkType(item.osn)" >руб</sup></div></div>
                            <div v-else :class="{black:!checkType(item.usn6)}">
                        {{ item.osn}}<sup class="price_reg" v-if="checkType(item.osn)" >руб</sup>
                    </div>
                    </div>
                    <div class="service_item_price">
                        <div v-if="isLowScreen" class="lowScreen">
                            <div>УСН 15%</div>
                            <div>{{ item.usn15}}
                            <sup class="price_reg" v-if="checkType(item.usn15)" >руб</sup></div>
                            </div>
                            <div v-else :class="{black:!checkType(item.usn6)}">
                        {{ item.osn}}<sup class="price_reg" v-if="checkType(item.usn15)" >руб</sup>
                    </div>
                    </div>
                    <div class="service_item_price">
                        <div v-if="isLowScreen" class="lowScreen">
                            <div>УСН 6%</div>
                            <div>
                            {{ item.osn}}
                            <sup class="price_reg" v-if="checkType(item.usn6)" >руб</sup></div></div>
                            <div v-else :class="{black:!checkType(item.usn6)}">
                        {{ item.osn}}<sup class="price_reg" v-if="checkType(item.usn6)" >руб</sup>
                    </div>
                    </div>
                </div>
                <div class="button_toggleService" v-if="isLowScreen">
                    <div @click="toggleService(index)" class="button_item"> 
                        <svg class="carousel__icon" viewBox="0 0 24 24" role="img" aria-label="Arrow pointing to the left"><title>Arrow pointing to the left</title><path d="M8.59 16.59L13.17 12 8.59 7.41 10 6l6 6-6 6-1.41-1.41z"></path></svg></div></div>

                </div>
            </div>


            </div>


            <section>

            <div class="cards_flex" v-if="!isMiddleScreen">
            <div class="cards" v-for="n in 3" :key="n">
                <div class="card_name"> <h2>{{ cardTitles[n] }}</h2></div>
                
                <div class="card" v-for="item in cards[n]" :key="item">
                    <div class="card_svg" v-if="n!==3">
                        <svg xmlns="http://www.w3.org/2000/svg" width="20" height="20" viewBox="0 0 20 20" fill="none">
  <path d="M6.98065 13.0136L2.2666 17.7276M9.74539 5.53483L8.44465 6.83556C8.33854 6.94167 8.28549 6.99472 8.22505 7.03687C8.1714 7.07429 8.11353 7.10526 8.05264 7.12915C7.98404 7.15605 7.91047 7.17077 7.76333 7.2002L4.70961 7.81094C3.91602 7.96966 3.51923 8.04902 3.33359 8.25823C3.17187 8.44049 3.09802 8.68439 3.13148 8.92575C3.16989 9.20279 3.45602 9.48893 4.02829 10.0612L9.93307 15.966C10.5053 16.5382 10.7915 16.8244 11.0685 16.8628C11.3099 16.8962 11.5538 16.8224 11.736 16.6607C11.9452 16.475 12.0246 16.0782 12.1833 15.2846L12.7941 12.2309C12.8235 12.0838 12.8382 12.0102 12.8651 11.9416C12.889 11.8807 12.92 11.8229 12.9574 11.7692C12.9995 11.7088 13.0526 11.6557 13.1587 11.5496L14.4594 10.2489C14.5273 10.181 14.5612 10.1471 14.5985 10.1175C14.6316 10.0912 14.6667 10.0674 14.7034 10.0465C14.7447 10.0228 14.7888 10.0039 14.877 9.96615L16.9556 9.07531C17.5621 8.81542 17.8653 8.68547 18.003 8.47549C18.1234 8.29185 18.1665 8.0681 18.1229 7.85288C18.073 7.60676 17.8398 7.3735 17.3732 6.90697L13.0873 2.62103C12.6208 2.15451 12.3875 1.92124 12.1414 1.87135C11.9262 1.82772 11.7024 1.87081 11.5188 1.99126C11.3088 2.12899 11.1788 2.43219 10.9189 3.03861L10.0281 5.11724C9.99031 5.20542 9.97142 5.24951 9.9478 5.29086C9.92682 5.32758 9.90307 5.36266 9.87676 5.39578C9.84714 5.43307 9.81322 5.46699 9.74539 5.53483Z" stroke="#4851FD" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"/>
</svg>
                    </div>
                    <div>
                    <div class="card_text">

                           <p class="card_title"> {{ item.title }}</p> <p class="card_minititle">{{ item.miniTitle }}</p>
                    </div>
                    <div class="card_boost">
                            {{ item.boost }}
                        </div>
                        </div>
                </div>
            
                <div class="card_bottom" v-if="cardBottoms[n].length>1"><div class="inner">{{cardBottoms[n]}}</div></div>
           
            </div>
        </div>
        <div v-else>
        <Carousel :items-to-show="1.2" :autoplay="2000" :wrap-around="true">
    <Slide v-for="slide in 3" :key="slide">
        <div class="cards_flex" style="height:100%; text-align: left;">
        <div class="cards" style="height:100%; text-align: left;">
                <div class="card_name"> <h2>{{ cardTitles[slide] }}</h2></div>
                
                <div class="card" v-for="item in cards[slide]" :key="item">
                    <div class="card_svg" v-if="slide!==3">
                        <svg xmlns="http://www.w3.org/2000/svg" width="20" height="20" viewBox="0 0 20 20" fill="none">
  <path d="M6.98065 13.0136L2.2666 17.7276M9.74539 5.53483L8.44465 6.83556C8.33854 6.94167 8.28549 6.99472 8.22505 7.03687C8.1714 7.07429 8.11353 7.10526 8.05264 7.12915C7.98404 7.15605 7.91047 7.17077 7.76333 7.2002L4.70961 7.81094C3.91602 7.96966 3.51923 8.04902 3.33359 8.25823C3.17187 8.44049 3.09802 8.68439 3.13148 8.92575C3.16989 9.20279 3.45602 9.48893 4.02829 10.0612L9.93307 15.966C10.5053 16.5382 10.7915 16.8244 11.0685 16.8628C11.3099 16.8962 11.5538 16.8224 11.736 16.6607C11.9452 16.475 12.0246 16.0782 12.1833 15.2846L12.7941 12.2309C12.8235 12.0838 12.8382 12.0102 12.8651 11.9416C12.889 11.8807 12.92 11.8229 12.9574 11.7692C12.9995 11.7088 13.0526 11.6557 13.1587 11.5496L14.4594 10.2489C14.5273 10.181 14.5612 10.1471 14.5985 10.1175C14.6316 10.0912 14.6667 10.0674 14.7034 10.0465C14.7447 10.0228 14.7888 10.0039 14.877 9.96615L16.9556 9.07531C17.5621 8.81542 17.8653 8.68547 18.003 8.47549C18.1234 8.29185 18.1665 8.0681 18.1229 7.85288C18.073 7.60676 17.8398 7.3735 17.3732 6.90697L13.0873 2.62103C12.6208 2.15451 12.3875 1.92124 12.1414 1.87135C11.9262 1.82772 11.7024 1.87081 11.5188 1.99126C11.3088 2.12899 11.1788 2.43219 10.9189 3.03861L10.0281 5.11724C9.99031 5.20542 9.97142 5.24951 9.9478 5.29086C9.92682 5.32758 9.90307 5.36266 9.87676 5.39578C9.84714 5.43307 9.81322 5.46699 9.74539 5.53483Z" stroke="#4851FD" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"/>
</svg>
                    </div>
                    <div>
                    <div class="card_text" >

                           <p class="card_title"> {{ item.title }}</p> <p class="card_minititle">{{ item.miniTitle }}</p>
                    </div>
                    <div class="card_boost">
                            {{ item.boost }}
                        </div>
                        </div>
                </div>
            
                <div class="card_bottom" v-if="cardBottoms[slide].length>1"><div class="inner">{{cardBottoms[slide]}}</div></div>
           
            </div>
        </div>
    </Slide>

    <template #addons>
      
      <Pagination />
    </template>
  </Carousel>
  
</div>
<div class="bottom_text">Все цены указаны в рублях и НДС не облагается на основании главы 26.2 НК РФ (УСНО)</div>

</section>
    
    </div>
        


    </div>
</section>
</template>

<script setup>
import { Carousel, Navigation, Slide,Pagination } from 'vue3-carousel'
import 'vue3-carousel/dist/carousel.css'
import {ref,onMounted,onUnmounted } from 'vue';
    const serviceItems =  ref([])
    const toggleService = (index)=>{
        console.log(serviceItems.value[index],index);
        serviceItems.value[index].classList.toggle("active")
        
    }
    const isLowScreen = ref(window.innerWidth < 420);
    const isMiddleScreen = ref(window.innerWidth < 769)
    const handleResize = () => {
        
        isLowScreen.value = window.innerWidth < 420;
        isMiddleScreen.value = window.innerWidth <769;
    };

    onMounted(() => {
      window.addEventListener('resize', handleResize);
    });

    onUnmounted(() => {
      window.removeEventListener('resize', handleResize);
    });


    

    const priceItems = [
        {title:"Обработка первичных документов (товарные накладные, счета-фактуры, акты выполненных работ, акты оказанных услуг, требования накладные, кассовые, банковские документы, авансовые отчеты, путевые листы)"},
        {title:"Составление локальных нормативных актов"},
        {title:"Проверка соответствия предоставленных документов нормам действующего законодательства"},
        {title:"Предоставление в письменной форме информации об отсутствующих документах и (или) документах, подлежащих замене в связи с некорректным оформлением"},
        {title:"Составление реестров и формировании архивных файлов с первичными документами"},
        {title:"Формирование бухгалтерских проводок, оборотно - сальдовых ведомостей, регистров бухгалтерского учета"},
        {title:"Формирование налоговых проводок, журналов учета полученных и выданных счетов – фактур, книг покупок и продаж, регистров налогового учета"},
        {title:"Составление, подача в налоговые органы, органы статистики бухгалтерской и налоговой отчетности"},
        {title:"Проведение сверок с контрагентами"},
        {title:"Консультирование по вопросам бухгалтерского и налогового учета"},
        {title:"Инвентаризации"},
        {title:"Проведение сверок с налоговыми органами"},
       ]
       const tabletitles = [{title:"Услуга",
        osn:"ОСН",
        usn15:"УСН 15%",
        usn6:"УСН 6%"},]
       const servicesPrices = [
        
        {title:"Ведение учета до 10 операций в месяц, включая подготовку и сдачу квартальной отчетности",
        osn:7000,
        usn15:5000,
        usn6:5000},
        {title:"Ведение учета от 11 до 20 операций в месяц, включая подготовку и сдачу квартальной отчетности",
        osn:9000,
        usn15:6000,
        usn6:6000},
        {title:"Ведение учета от 21 до 50 операций в месяц, включая подготовку и сдачу квартальной отчетности",
        osn:11000,
        usn15:9000,
        usn6:9000},
        {title:"Ведение учета от 51 до 100 операций в месяц, включая подготовку и сдачу квартальной отчетности",
        osn:18000,
        usn15:15000,
        usn6:15000},
        {title:"Ведение учета от 101 до 200 операций в месяц, включая подготовку и сдачу квартальной отчетности",
        osn:23000,
        usn15:20000,
        usn6:20000},
        {title:"Ведение учета от 201 до 300 операций в месяц, включая подготовку и сдачу квартальной отчетности",
        osn:27000,
        usn15:25000,
        usn6:25000},
        {title:"Ведение учета от 301 до 400 операций в месяц, включая подготовку и сдачу квартальной отчетности",
        osn:35000,
        usn15:30000,
        usn6:30000},
        {title:"Ведение учета свыше 400 операций в месяц",
        osn:"Договорная",
        usn15:"Договорная",
        usn6:"Договорная"},

        

       ]



       const cardTitles = {1:"Сопровождение камеральных и выездных налоговых проверок",2:"Услуги по правовому обслуживанию",3:"Дополнительно к расчетной цене устанавливаются надбавки"}
       const firstCard = [
        {title:"Консультирование по вопросам, которые возникают при прохождении налоговых проверок",miniTitle:"",boost:""},
       {title:"Проверка налоговых деклараций и имеющихся документов",miniTitle:"",boost:""},
       {title:"Подготовка документов к проверке",miniTitle:"(инвентаризация, сбор, ксерокопирование, заверение)",boost:""},
       {title:"Участие в проверке ИФНС ",miniTitle:"(сопровождение проверки)",boost:""},
       {title:"Разработка договоров в рамках подготовки к проверке",miniTitle:"",boost:""},
       {title:"Представительство интересов клиента в государственных органах",miniTitle:"",boost:""},
       {title:"Составление письменного возражения на акт проведенной проверки",miniTitle:"",boost:""},
       {title:"Составление пояснительных записок, ответ, информационных писем на акты проведенных проверок",miniTitle:"",boost:""},
       ]
       const secondCard = [
        {title:"Проверка соответствия внутренних документов требованиям законодательствам",miniTitle:"",boost:""},
       {title:"Организация и ведение претензионной работы по материалам, подготавливаемой бухгалтерией",miniTitle:"",boost:""},
       {title:"Представления интересов в суде, а также в других органах при рассмотрении правовых вопросов, подготовка процессуальной позиции и иную информацию для надлежащего качества ведения дела и направления ее в суд",miniTitle:"",boost:""},
       {title:"Подготовка и оформление различного рода договоров, организация контроля исполнения договоров ",miniTitle:"",boost:""},
       {title:"Помощь в организации и осуществлении контроля над соблюдением установленного действующего законодательства РФ порядка осуществления коммерческой деятельности",miniTitle:"",boost:""},
       {title:"Помощь в организации и ведении претензионной работы по материалам, подготавливаемым бухгалтерией, оказание методической помощи в этой работе, если она ведется другими подразделениями Заказчика",miniTitle:"",boost:""},
       {title:"Консультация, заключение, справки по правовым вопросам, оказание помощи в своевременном и законном разрешении предложений, заявлений и жалоб",miniTitle:"",boost:""}
       
       ]
       const thirdCard = [
        {title:"Внешнеэкономическая деятельность",miniTitle:"",boost:"от +5 % до +25%"},
       {title:"Различные ставки НДС при реализации",miniTitle:"",boost:"от +5 % до +10%"},
       {title:"Составление первичной документации",miniTitle:"",boost:"от +5 % до +20%"},
       {title:"Введение делопроизводства ",miniTitle:"(учет и регистрация договоров, входящей и исходящей документации, архивирование дел) ",boost:"от +5 % до +20%"},
       {title:"Автоматизация учета, обновление и доработка программ",miniTitle:"",boost:"от +5 % до +25%"},
       {title:"IT услуги",miniTitle:"(сетевое оборудование, оборудование рабочих мест, система хранения данных, сети, телефония, телекоммуникации, сетевые сервисы, база данных, автоматизация бизнес – процессов, администрирование, постоянная поддержка)",boost:"+15 %"}
      
       
       ]
       const cards = {
        1:firstCard,
        2:secondCard,
        3:thirdCard
       }
      
     const  checkType = (osn)=>{

        console.log(typeof(osn));
        return typeof(osn)!=="string"
     }
      const cardBottoms = {1:"+ 25% к итоговой стоимости бухгалтерского обслуживания в квартал за проверяемый налоговый период",2:"+5% к итоговой стоимости бухгалтерского обслуживания в квартал",3:""}
</script>


<style lang="scss" scoped>


//price_list    
.price_description{
    
    height: auto;
    border-radius: 32px;
    background: #F2F7FC;
    margin-top: 35px;
}
.price_description_title{
    color: #4851FD;
    padding: 32px;
    font-size: 18px;
    font-style: normal;
    font-weight: 600;
    line-height: 28px; 
            @media (max-width:420px) {
                font-size: 12px;
                padding: 12px;
            }
}
.price_items{
    display: flex;
    flex-wrap: wrap;
}
.price_item{
    display:flex;
    justify-content: left;
    
    
        padding: 32px;
        
        
        gap: 24px;
        flex: 0 0 calc(100%/2);
        @media (max-width:768px) {
            flex:0 0 calc(100%);
        }
        @media (max-width:420px) {
            
            padding: 12px;
            gap: 5px;
        }
       
        
}
.price_item_title{
    color: #0A2641;

font-size: 14px;
font-style: normal;
font-weight: 600;
line-height: 20px; 
    @media (max-width:420px) {
            font-size: 12px;
            
        }
}
.black{
    color: #0A2641;

font-size: 16px;
font-style: normal;
font-weight: 600;
line-height: 24px; 
}
//service
.blue{
    color: #4851FD !important;

    text-transform: uppercase !important;
}
.service_item{
    display: flex;
    justify-content: space-between;
    margin-top: 20px;
    position: relative;
    @media (max-width:420px) {
        flex-direction: column;
    }

}
.service_item_prices{
    
    display: flex;
    
    
    @media (max-width:420px) {
        
        display: none;
    }
}
.service_item_title{
    padding-right:30px;
}
.active{
    @media (max-width:420px) {
        display: block;
    } 
}
.button_toggleService{
    display: block;
    position: absolute;
    top: 0;
    right:15px;
    z-index: 50;
    
    width: 20px;
    height: 20px;
    border-radius: 50%;
    

    background-color: #5F83A7;
  } 
  .button_item{
    transform: rotate(90deg);
    margin-right: 6px;
    margin-top:-3px;
  }

.lowScreen{
    display: flex;
    justify-content: space-between;
}
.price_reg{
    color: #0A2641;

font-size: 18px;
font-style: normal;
font-weight: 600;
line-height: 24px;
}
.service_item_title{
   
    color: #0A2641;

font-size: 12px;
font-style: normal;
font-weight: 600;
line-height: 20px; 
    flex: 1 0 calc(100% - 360px);
    @media (max-width:769px) {
       
    }
}
.service_item_price{
    
    width: 120px;
    color: var(--blue2);
    @media (max-width:769px) {
        width: 100%;
    }
font-size: 18px;
font-style: normal;
font-weight: 600;
line-height: 24px; 
}
//card
.cards_flex{
    display: flex;
    gap: 2rem;
    margin-right: 40px;

}
.cards{
    
    display: flex;
width: 451px;

padding: 32px;
flex-direction: column;

gap: 24px;


border-radius: 32px;
background: #F2F7FC;
position: relative;
@media (max-width:768px) {
            width: 100%;
            margin-right: 30px;
        }
        @media (max-width:420px) {
            padding: 0px;
           
            
            flex: 1 0 100%;

        }
       


}
.card_name{
    color: var(--blue2);

font-size: 18px;
font-style: normal;
font-weight: 600;
line-height: 28px; 
@media (max-width:420px) {
            font-size: 14px;

        }
}
.card{
    display: flex;
    justify-content: left;
    
    
    
}
.card_title{
    color: #000;

font-size: 14px;
font-style: normal;
font-weight: 600;
line-height: 20px; 
@media (max-width:420px) {
    font-size: 12px;
            
        } 

}
.card_minititle{
    color: #5F83A7;

font-size: 12px;
font-style: normal;
font-weight: 600;
line-height: 20px;
}
.card_boost{
    display: block;
    color: #4851FD;

font-size: 18px;
font-style: normal;
font-weight: 600;
line-height: 20px; 
}
.card_bottom{
   
margin-top: auto;


}
.bottom_text{
    color: #5F83A7;

font-size: 12px;
font-style: normal;
font-weight: 600;
line-height: 20px; 
margin-top:20px;
}

.inner{
    padding: 24px;
color:var(--white);
    border-radius: 24px;
background: #4851FD;
}
</style>