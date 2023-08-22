<template>
    <div class="container">
        <div class="inner_container">
            <div class="footer">
                <div class="footer_inner">
                    <div class="footer_logo">
                        <div class="logo_block">
                        <div class="logo blue"></div>
                        <div class="logo orange"></div>

                        
                    </div>
                    <div class="logo_text">Pascal</div>

                    </div>
                    <div class="footer_list">
                        <div>
                        <div class="footer_text">Наши преимущества</div>
                        <div class="footer_text">Наши услуги</div>
                        <div class="footer_text">Прайс-лист на бухгалтерские услуги</div>
                    </div>
                    <div>
                        <div class="footer_text">Новости</div>
                        <div class="footer_text">Отзывы клиентов</div>
                        <div class="footer_text">Политика конфиденциальности</div>
                    </div>
                    </div>
                    <div class="footer_connection">
                        <div class="footer_number">
                            8 (812) 603-71-79
                            <br>
                            <a href="">Обратный звонок</a>
                        </div>
                        <div class="footer_links">
                            <div class="footer_link">
                                <img src="../assets/links/Telegram.svg" alt="">
                            </div>
                            <div class="footer_link">
                                <img src="../assets/links/Group597.svg" alt="">
                            </div>
                            <div class="footer_link">
                                <img src="../assets/links/Twitter.svg" alt="">
                            </div>
                            <div class="footer_link">
                                <img src="../assets/links/Facebook.svg" alt="">
                            </div>
                            <div class="footer_link">
                                <img src="../assets/links/vkontakte.svg" alt="">
                            </div>
                        </div>
                    </div>

                </div>
            </div>
            <div class="footer_tags">
                <div class="footer_tag">ООО "ПАСКАЛЬ"</div>
                <div class="footer_tag">ИНН 7816427865</div>
                <div class="footer_tag">КПП 781101001</div>
                <div class="footer_tag">ОГРН 1079847083755</div>
                <div class="footer_tag">ОКПО 83759627</div>
                <div class="footer_tag">Расчетный счет 40702810455100001938</div>
                <div class="footer_tag blue_text">Генеральный директор Кремницына Елена Николаевна</div>
                <div class="footer_tag">Банк: СЕВЕРО-ЗАПАДНЫЙ БАНК ПАО СБЕРБАНК</div>
                <div class="footer_tag">БИК 044030653</div>
                <div class="footer_tag">Корр. счет 30101810500000000653</div>
                <div class="footer_tag">Юридический адрес: 192012, Санкт-Петербург г, ул Ново-Александровская, д. 14, литер А, 54-Н, КОМ. 3</div>
            </div>
        </div>

    </div>
</template>

<script setup>

</script>

<style lang="scss" scoped>
    .footer_inner  {
        display: flex;
        justify-content: space-between;
            @media (max-width:768px) {
            display: block;
        }
    }
    .footer_list{
        display: flex;
        justify-content: space-between;
            @media (max-width:420px) {
            display: block;
        }
    }
    .footer_text{
        color: #0A2641;
        font-size: 16px;
        
        font-weight: 600;
        line-height: 28px; 
        padding-right: 30px;
        margin-bottom:30px ;
    }
    a{
        color: #4851FD;

        font-size: 14px;
       
        font-weight: 600;
        line-height: 28px; 
        text-decoration: none;
    }



 .footer_logo{
        display: flex;
        justify-content: left;
        position: relative;
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
            padding-left: 35px;

            color: #0A2641;
            
            font-size: 24px;
            
            font-weight: 600;
            line-height: normal;
        }
        .footer_links{
            display: flex;
            justify-content: left;
        }
        .footer_number {
            color: #0A2641;
            font-size: 24px;
            
            font-weight: 600;
            line-height: 28px; 

        }
        .footer_connection {
                @media (max-width:768px) {
                    display: flex;
                    justify-content: space-between;
                }
            @media (max-width:420px) {
                display: block;
        }
        }

        .footer_tags{
            display: flex;
            justify-content: space-between;
            flex-wrap: wrap;
            gap: 2rem;
        }
        .footer_tag{
        
            flex: 0 0 calc(100%/6);
            color: #5F83A7;
           
            font-size: 11px;
            
            font-weight: 600;
            line-height: 16px; 
            opacity:0.9;

        }
        .blue_text{
            color:#4851FD
        }
</style>