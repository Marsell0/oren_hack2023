<script>
import BlueButton from './components/BlueButton.svelte'
import WhiteButton from './components/WhiteButton.svelte'
import Profile from './pages/Profile.svelte';

import axios from 'axios'
let res
let login = ''
let password = ''

let type = 'submit'

let params
// let url = 'https://0435-176-28-64-201.ngrok-free.app/api'
let url = 'https://82e7-145-255-21-225.ngrok-free.app'

async function postReg(){
  let email = login
  let pass = password
  params = {
      'email': email,
      'password': pass
    } 
  console.log(params);
  res = await axios.post(url+"/signup", params,
  {
    headers: {
      'ngrok-skip-browser-warning': '69420',
      'Content-Type': 'application/json'
    }
  })
}

let token, isError
async function postAuth(){
  let email = login
  let pass = password
  params = {
      "email": email,
      "password": pass
    } 
  console.log(params);
  res = await axios.post(url+"/users/sign_in", params,
  {
    headers: {
      'Content-Type': 'application/json'
    }
  }).catch(() => {
    isError = true
  })
  console.log(res);
  res = res['data']
  token = res['tokenPair']
  localStorage.role = res['role']
  localStorage.token = token['accessToken']
  localStorage.refreshToken = token['refreshToken']
  location.reload()
}

function logout(){
  localStorage.clear()
  location.reload()
}
</script>

<div class="wrapper">
  <div class="header">
    <div class="header__wrapper">
      <div class="header__logo">
        <img src="" alt="" class="logo__img">
        <p class="logo__text">nazvanie</p>
      </div>
      <ul class="header__menu">
        <li class="menu__item">ТАРИФЫ</li>
        <li class="menu__item">ВНЕДРЕНИЕ</li>
        <li class="menu__item">ОТЗЫВЫ</li>
      </ul>
      <div class="header__buttons">
        {#if localStorage.role}
          <p>{localStorage.role}</p>
          <button class="buttons__exit" on:click={logout}>Выход</button>
        {:else}
          <!-- <BlueButton {type}>
            Вход
          </BlueButton> -->
          <WhiteButton {type}>
            Новый портал
          </WhiteButton>
        {/if}
      </div>
    </div>
  </div>

  {#if localStorage.role}
    <Profile></Profile>
  {:else}
    <div class="auth">
      <div class="auth__wrapper">
        <p class="auth__title">Вход</p>
        <form on:submit|preventDefault={postAuth} action="" class="auth__form">
          <input class="form__input" type="text" bind:value={login} placeholder="email">
          <input type="password" bind:value={password} class="form__input" placeholder="password">
          <p class="form__forgot">Забыли пароль?</p>
          <div style="display: flex; justify-content: center;">
            <input type="submit" class="form__btn" value="Войти">
          </div>
          
          {#if isError}
            <p>{res}</p>
          {/if}
        </form>
      </div>
      
    </div>
  {/if}

</div>

<style scoped>
  .wrapper{
    display: flex;
    flex-direction: column;
    

  }
  .header{
    border: 1px solid #F0F0FF;
    background: #FFF;
    font-family: 'SF';

  }
  .header__wrapper{
    display: flex;
    flex-direction: row;
    padding: 1% 0;
    justify-content: space-between;
    max-width: 1533px;
    max-height: 4320px;
    margin: 0% 15%;
  }
  .header__logo{
    display: flex;
    flex-direction: row;
    align-items: center;
  }
  .logo__img{

  }
  .logo__text{
    color: var(--light-mode-primary-700, #271FE0);
font-feature-settings: 'clig' off, 'liga' off;
font-size: 16px;
font-style: normal;
font-weight: 500;
line-height: 24px; /* 150% */
text-transform: uppercase;
  }
  .header__menu{
    display: flex;
    flex-direction: row;
    align-items: center;
  }
  .menu__item{
    padding: 0 8%;
    color: var(--light-mode-primary-700, #271FE0);
font-size: 16px;
font-style: normal;
font-weight: 500;
line-height: 24px; /* 150% */
text-transform: uppercase;
  }
  .header__buttons{
    display: flex;
    flex-direction: row;
  }
  .buttons__exit{
    display: inline-flex;
padding: 10px var(--16, 16px);
justify-content: center;
align-items: center;
border-radius: 4px;
border-color: #FCECEA;
background:#FCECEA;
color: #EE5E52;

font-size: 14px;
font-style: normal;
font-weight: 600;
line-height: 16px; /* 114.286% */
  }
  .buttons__btn{
    
  }

  .auth{
    display: flex;
    flex-direction: column;
    margin: 0px auto;
    max-width: 590px;
    border-radius: 35px;
    border: 1px solid #DCDCE4;
    background: #FFF;
    font-family: 'SF';
  }
  .auth__wrapper{
    padding: 70px 90px;
  }
  .auth__title{
    color: var(--light-mode-primary-700, #271FE0);
    font-feature-settings: 'clig' off, 'liga' off;
    margin-bottom: 20%;

    /* H1 */
    font-size: 32px;
    font-style: normal;
    font-weight: 600;
    line-height: 40px; /* 125% */
  }
  .auth__form{
    display: flex;
    flex-direction: column;
  }
  .form__input{
    display: flex;
    padding: 15px 21px;
    align-items: center;
    border-radius: 5px;
    border: 1px solid #DCDCE4;
    background: #FFF;
    margin: 10px 0px;
  }
  .form__forgot{
    display: inline-flex;
    padding: 0px 8px;
    justify-content: end;
    gap: 8px;
    color: var(--light-mode-primary-500, #7B79FF);
    font-feature-settings: 'clig' off, 'liga' off;
    font-family: SF Pro Text;
    font-size: 12px;
    font-style: normal;
    font-weight: 400;
    line-height: 20px; /* 166.667% */
    cursor: pointer;
    transition: 0.5s ease all;
  }
  .form__forgot:hover{
    transition: 0.5s ease all;
    color: #4945FF;
  }
  .form__btn{
    display: flex;
    padding: 15px 100px;
    justify-content: center;
    align-items: center;
    border-radius: 10px;
    border: 1px solid #4945FF;
    background: #4945FF;
    color: #fff;
    max-width: 245px;
    transition: 0.5 ease all;
  }
  .form__btn:hover{
    transition: 0.5 ease all;
    cursor: pointer;
    border-radius: 10px;
    border: 1px solid #7B79FF;
    background: #7B79FF;
    box-shadow: 0px 1px 2px 0px rgba(198, 228, 246, 0.05);
  }
  .main{

  }
  
  .footer{

  }
</style>