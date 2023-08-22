<template>
    <div class="header_modal">
        
                <div class="modal">
                    <div class="button_close" @click="closeModal(false)">
                        <svg xmlns="http://www.w3.org/2000/svg" width="24" height="24" viewBox="0 0 24 24" fill="none">
  <g opacity="0.4">
    <path d="M18 6L6 18M6 6L18 18" stroke="white" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"/>
  </g>
</svg>
                    </div>
                <div class="modal_inner">
                    <div class="modal_title">

                        Оставьте заявку <br>и мы перезвоним

                    </div>
                    <div>
                    <div class="modal_form">
                        <label for="name">Имя</label>
                        <input type="text" placeholder="Введите имя" v-model="name" >
                        <label for="name">Телефон</label>
                        <input ref="el" type="text" placeholder="Введите телефон" v-model="number" >
                       

                    </div>
                    <div class="modal_footer">
                        <div class="modal_policy">
                            Нажимая на кнопку, я даю согласие на обработку персональных данных в соответствии с 
                            <a href="">Политикой конфиденциальности</a>
                        </div>
                        <div class="button_modal" @click="sendRequest()">Отправить</div>
                    </div>

                </div>
                </div>



            </div>
            
            </div>
            <div  class="modalBackground">
        </div>
           
        


</template>


<script setup>
import {ref} from 'vue'
import { useIMask } from 'vue-imask';
const { el, masked } = useIMask({
        mask: '+7(900)000-00-00',
        radix: '.',
        lazy:true
      })

      const name = ref('')
      const number = ref('')
const closeModal=(bool)=>{

      
emit('closeHeaderModal',bool)

}
const emit = defineEmits(['closeHeaderModal'])
const sendRequest=()=>{
    console.log(name.value,number.value);
    if(name.value.length>4&& number.value.length==16){
        console.log(name,number);
        emit('closeHeaderModal',false)
        alert(`'your name:${name} and number:${number}'`)
        
    }
    
}

</script>

<style lang="scss" scoped>


.header_modal{
    position: absolute;
    top: 50%;
    z-index: 80;
    left:50%;
    transform:translate(-50%, -50%);
}
.button_close{
    position: absolute;
    right: 20px;
    top: 20px;
    cursor: pointer;
}
.modal{
    width: 507px;
height: 568px;
position: relative;
@media (max-width:500px) {
            width: 100vw;
            height: 100vh;
    }



border-radius: 32px;
background: conic-gradient(from 206deg at 27.86% 63.07%, #4851FD 119.0906274318695deg, #FF6A2A 272.8011703491211deg), linear-gradient(169deg, #4851FD 0%, #FF6A2A 100%), #4851FD;
margin-top: 50px;
@media (max-width:768px) {
    
background: conic-gradient(from 219deg at 69.61% 25.48%, #4851FD 46.87499821186066deg, #FF6A2A 183.75000715255737deg), linear-gradient(169deg, #4851FD 0%, #FF6A2A 100%), #4851FD;


height: auto;
    }
    
}

.modal_inner{
    
        padding: 50px;
    @media (max-width:768px) {
            display: block;
    }
    
}
.modal_title{
    color: #FFF;

    font-size: 36px;
    
    font-weight: 700;
    line-height: 48px; 
}

label{
    text-transform: uppercase;
}
label, input{
    color: var(--white);
    

    font-size: 14px;
    
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
    @media (max-width:500px) {
            display: block;
    }
}
.modal_policy,a{
    color: var(--white);

    font-size: 14px;
    
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

//modalBackground
.modalBackground{
        position: fixed;
        width:200%;
        height: 200% ;
        background-color: black;
        z-index:70;
        opacity: 0.5;
        left:-500px;
        top: 0;

}
</style>