<template>
    <div class="container">
        <div class="inner_container">
            <div class="modal">
                <div class="modal_inner">
                    <div class="modal_title">

                        Задайте вопрос специалистам

                    </div>
                    <div>
                    <div class="modal_form">
                        <label for="name">Имя</label>
                        <input type="text" placeholder="Введите имя">
                        <label for="name">Телефон</label>
                        <input type="text" placeholder="Введите телефон">
                        <label for="text">Вопрос</label>
                        <textarea name="text" id="" cols="30" rows="10" placeholder="Введите вопрос..." class="modal_question"></textarea>

                    </div>
                    <div class="modal_footer">
                        <div class="modal_policy">
                            Нажимая на кнопку, я даю согласие на обработку персональных данных в соответствии с 
                            <a href="">Политикой конфиденциальности</a>
                        </div>
                        <div class="button_modal">Отправить</div>
                    </div>

                </div>
                </div>



            </div>

            <div class="map">
                <div style="position:relative;overflow:hidden;"><a href="https://yandex.ru/maps/2/saint-petersburg/?utm_medium=mapframe&utm_source=maps" style="color:#eee;font-size:12px;position:absolute;top:0px;">Санкт‑Петербург</a><a href="https://yandex.ru/maps/2/saint-petersburg/stops/station__9805940/?ll=30.443725%2C59.931213&tab=overview&utm_medium=mapframe&utm_source=maps&z=14.74" style="color:#eee;font-size:12px;position:absolute;top:14px;">Ладожская — Яндекс Карты</a><iframe src="https://yandex.ru/map-widget/v1/?ll=30.443725%2C59.931213&masstransit%5BstopId%5D=station__9805940&mode=masstransit&tab=overview&z=14.74" width="100%" height="400" frameborder="1" allowfullscreen="true" style="position:relative;"></iframe></div>
            </div>
        </div>

    </div>
</template>

<script setup>


</script>

<style lang="scss" scoped>
.modal{
    width: 100%;
height: 700px;
flex-shrink: 0;
border-radius: 32px;
background: conic-gradient(from 206deg at 27.86% 63.07%, #4851FD 119.0906274318695deg, #FF6A2A 272.8011703491211deg), linear-gradient(169deg, #4851FD 0%, #FF6A2A 100%), #4851FD;
margin-top: 50px;
@media (max-width:768px) {
    
background: conic-gradient(from 219deg at 69.61% 25.48%, #4851FD 46.87499821186066deg, #FF6A2A 183.75000715255737deg), linear-gradient(169deg, #4851FD 0%, #FF6A2A 100%), #4851FD;


height: auto;
    }
    
}

.modal_inner{
    display: flex;
    justify-content: space-between;
    padding: 50px;
        @media (max-width:768px) {
            display: block;
    }
    
}
.modal_title{
    color: #FFF;

    font-size: 36px;
    font-style: normal;
    font-weight: 700;
    line-height: 48px; 
}

label{
    text-transform: uppercase;
}
label, input{
    color: var(--white);
    font-size: 14px;
    font-style: normal;
    font-weight: 600;
    line-height: 28px; 
    
}
input,textarea{
    display: block;
    width: 90%;
    height: 60px;
    border-radius: 32px;
    background: rgba(255, 255, 255, 0.10);
    margin-bottom: 50px;
    &::placeholder{
        font-size: 18px;
        opacity: 0.5;
        padding: 15px;
        

        font-style: normal;
        font-weight: 600;
        line-height: 28px;
    }
}

.modal_question{
    
        height: 148px;

}


.modal_footer{
    display: flex;
    justify-content: space-between;
    width: 90%;
    @media (max-width:420px) {
            display: block;
    }
}
.modal_policy,a{
    color: var(--white);

    font-size: 14px;
    font-style: normal;
    font-weight: 600;
    line-height: 20px; 
    opacity: 0.5;
    margin-bottom: 20px;
}

.button_modal{
    padding: 18px 32px;
    border-radius: 32px 0px;
    background: #4851FD;  
    max-width: 200px;  
    max-height: 60px;
    color: var(--white);
    text-align: center;
   
}


</style>