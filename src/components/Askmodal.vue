<template>
    <section class="footer_modal">
    <div class="container">
        <div class="inner_container">
            <div class="modal">
                <div class="modal_inner">
                    
                    <div class="modal_title">

                        Задайте вопрос специалистам

                    </div>
                    <div>
                    <div class="modal_form">
                        <label for="name" >Имя</label>
                        <input class="modal_form_control" type="text" placeholder="Введите имя" v-model="state.name" @input="filterInput()" >
                        <div ref="nameError" v-for="error in v$.name.$errors">{{error.$message}}</div>
                        <label for="name">Телефон</label>
                        
                        <input class="modal_form_control" type="text" placeholder="+7"  
                        ref="el" @input="updateValue()" maxlength="18"  id="phoneNumber">
                        <div v-for="error in v$.phoneNumber.$errors">{{error.$message}}</div>
                        
                        
                        <label for="text">Вопрос</label>
                        <textarea class="modal_form_control modal_question"  name="text" id="" maxlength="400" v-model ="state.question" cols="30" rows="10" placeholder="Введите вопрос..." ></textarea>
                        <div v-for="error in v$.question.$errors">{{error.$message}}</div>
                    </div>
                    <div class="modal_footer">
                        <div class="modal_policy">
                            Нажимая на кнопку, я даю согласие на обработку персональных данных в соответствии с 
                            <a href="">Политикой конфиденциальности</a>
                        </div>
                        <div class="button_modal" @click="submit()" v-if="!loadingButton">Отправить</div>
                        <div class="lds-dual-ring" v-if="loadingButton"></div>
                    </div>

                </div>
                </div>



            </div>

            <div class="map">
                <div style="position:relative;overflow:hidden;"><a href="https://yandex.ru/maps/2/saint-petersburg/?utm_medium=mapframe&utm_source=maps" style="color:#eee;font-size:12px;position:absolute;top:0px;">Санкт‑Петербург</a><a href="https://yandex.ru/maps/2/saint-petersburg/stops/station__9805940/?ll=30.443725%2C59.931213&tab=overview&utm_medium=mapframe&utm_source=maps&z=14.74" style="color:#eee;font-size:12px;position:absolute;top:14px;">Ладожская — Яндекс Карты</a><iframe src="https://yandex.ru/map-widget/v1/?ll=30.443725%2C59.931213&masstransit%5BstopId%5D=station__9805940&mode=masstransit&tab=overview&z=14.74" width="100%" height="400" frameborder="1" allowfullscreen="true" style="position:relative;"></iframe></div>
            </div>
        </div>

    </div>
</section>
</template>

<script setup>
import { reactive,ref,onMounted } from 'vue';
import { useVuelidate } from '@vuelidate/core'
import { required, email,minLength } from '@vuelidate/validators'
import { useIMask } from 'vue-imask'


const { el, masked } = useIMask({
        mask: '+{7}(000) 00 000 00',
        lazy:true
      });
      
    console.log(masked);
   const  updateValue =()=>{
        // state.phoneNumber = masked.value
        console.log(state.phoneNumber,state.phoneNumber.length);
        console.log(masked.value);
    }



const state = reactive({
      name: '',
    //   mail: '',
      phoneNumber:'',
      question:'',
      
    })
   
    
        const rules = {
            name: { required,minLength:minLength(2) },
            question: { required,minLength:minLength(5) },
            phoneNumber:{required,minLength:minLength(2)}, 
            // mail: { required }, 
     
    }
    const filterInput=()=>{
        state.name = state.name.replace(/[^a-zа-яё]/gi, '')
       
        
    }
const v$ = useVuelidate(rules, state)


const  submit = async () => {
      const result = await v$.value.$validate()
      state.phoneNumber = masked.value
      console.log(state.phoneNumber);
      if (!result) {
        // notify user form is invalid
        console.log(result);
        console.log(v$.value.$errors);
        return
      }
      else{
        loadingButton.value=true
        let inputNumber = document.getElementById('phoneNumber')

        setTimeout(() => {
            loadingButton.value=false
            state.name =''
            
            state.phoneNumber=''
            state.question=''
            inputNumber.value = ''
            v$.value.$reset()
        }, 2000);
      }
      // perform async actions
      
    }
  const loadingButton = ref(false)
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
    
    font-weight: 700;
    line-height: 48px; 
}
//forms
.modal_form_control{
    display: block;
    width: 90%;
    height: 60px;
    border-radius: 32px;
    padding-left: 15px;
    color: var(--white);
    
    font-weight: 600;
    line-height: 28px;
    background: rgba(255, 255, 255, 0.10);
    margin-bottom: 50px;
    border: none;
    outline:none;
    
    font-size: 18px;
    &::placeholder{
        // font-size: 18px;
        opacity: 0.5;
        
        color: inherit;

        
    }
    &:focus{
        color: yellowgreen;
        padding-left: 15px;
        border: none;
        border: 5px solid yellowgreen;
        &::placeholder{
            padding-left: 0px;
        }
    }
}

label{
    text-transform: uppercase;
    color: var(--white);
    font-size: 14px;
    
    font-weight: 600;
    line-height: 28px; 
    
}


.modal_question{
        
        height: 148px;
        resize: vertical;

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
    cursor: pointer;
}
//loading
.lds-dual-ring {
  display: inline-block;
  width: 80px;
  height: 80px;
}
.lds-dual-ring:after {
  content: " ";
  display: block;
  width: 25px;
  height: 25px;
  margin: 8px;
  border-radius: 50%;
  border: 3px solid #fff;
  border-color: #fff transparent #fff transparent;
  animation: lds-dual-ring 1.2s linear infinite;
}
@keyframes lds-dual-ring {
  0% {
    transform: rotate(0deg);
  }
  100% {
    transform: rotate(360deg);
  }
}
.map{
    margin-top: 3rem;
}


</style>