
<template>
  <div class="container-lg bg-zinc-950 h-screen w-full"> 
    <div v-show="login_page" class="flex flex-col items-center justify-center h-full w-full"> 
      <div class="text-center"> 
        <h1 class="title"> HELLO WELCOME </h1>
        <p class="subtitle"> PLEASE ENTER PASSWORD </p>
        <input v-model="password" class="h-12 w-80"/>
        <button @click="checkPassword" class="subtitle h-12 w-20 bg-blue-700 text-white ml-4"> ENTER </button>
        <p class="error-message mt-4"> {{ err_mess ? err_mess : '&nbsp;'  }}</p>
      </div>
    </div>

    <div v-show="loader" class="container-lg bg-zinc-950 h-screen w-full"> 
      <div class="flex flex-col items-center justify-center h-full w-full"> 
        <span class="loader"></span>
      </div>
    </div>

    <div v-show="view_content"> 
      <div class="relative">
        <h1 class="title absolute top-56 md:inset-x-1/3 lg:inset-x-1/3 text-center p-4"> HELLO REIGNE I KNOW IT'S YOU! </h1>
        <img src="/public/bg-motor.gif" class="h-screen w-screen"/>
      </div>
      <div class="container-lg bg-zinc-950 h-full w-full">
        <div class="grid grid-rows-1 grid-cols-1 sm:grid-cols-1 md:grid-cols-3 lg:grid-cols-3 text-center"> 
          <div class="flex justify-center items-center"> 
            <img src="/public/driver.png" class="w-2/3"/> 
          </div>
          <div> 
            <div class="flex justify-center items-center"> 
              <video muted class="h-3/4" controls>
                <source src="/public/vid.mov" type="video/mov"/>
              </video>
            </div>
            <p class="subtitle2 mt-4 text-center"> 
              How are you baby! hihihi sana magustuhan mo ang munting gift ko para sayo hahaha, almost 4 months
              na din simula nung nagkakilala tayo. Nag simula sa simple banat ko sa bio hahaha charot. Kumusta ka
              naman baby sana lagi kang nasa maayos na lagay. Wag mong papabayaan sarili mo. Wag ka siguro magalit sakin
              kung tutulungan kitang alagaan sarili mo hahahaha. Lagi mong tatandaan baby andito lang ako aaah!
              Pinapangako ko sayo, iingat ko puso mo. Ipaparamdam ko sayo yung pagmamahal na nararapat para sayo.
              I miss you and i love you.
            </p>
          </div>
          <div class="flex justify-center items-center"> 
            <img src="/public/car.png" class="w-2/3"/>  
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script setup>
import { ref } from 'vue';

const password = ref('')
const view_content = ref(false)
const err_mess = ref('')
const loader = ref(false)
const login_page = ref(true)

const checkPassword = () => {
  console.log('Password entered:', password.value);

  if(password.value === '16'){
    login_page.value = false
    loader.value = true
    setTimeout(() => {
      view_content.value = true
      err_mess.value = ''
      loader.value = false
    }, 3000); 


  } else {
    login_page.value = true
    password.value = ''
    view_content.value = false
    err_mess.value = 'INVALID PASSWORD, TRY AGAIN!'
  }
}

</script>

<style>
</style>
