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
let url = 'https://0435-176-28-64-201.ngrok-free.app/api'

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
      'email': email,
      'password': pass
    } 
  console.log(params);
  res = await axios.post(url+"/signin", params,
  {
    headers: {
      'ngrok-skip-browser-warning': '69420',
      'Content-Type': 'application/json'
    }
  }).catch(() => {
    isError = true
  })
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
        <!-- <div class="buttons__btn">
          <BlueButton {type}>
            Вход
          </BlueButton>
        </div>
        <div class="buttons__btn">
          <WhiteButton {type}>
            Новый портал
          </WhiteButton>
        </div> -->
        {#if localStorage.role}
          <p>{localStorage.role}</p>
          <button on:click={logout}>Выход</button>
        {:else}
          <BlueButton {type}>
            Вход
          </BlueButton>
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
          <input type="submit" class="form__btn" value="Войти">
          {#if isError}
            <p>{res}</p>
          {/if}
        </form>
      </div>
      
    </div>
  {/if}

</div>

<style>
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
    padding: 2% 0;
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
  .buttons__btn{
    
  }

  .auth{
    display: flex;
    flex-direction: column;
    margin: 0px auto;
    border-radius: 35px;
    border: 1px solid #DCDCE4;
    background: #FFF;
    font-family: 'SF';
  }
  .auth__wrapper{
    padding: 20% 20%;
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
  }
  .form__btn{
    display: inline-flex;
    padding: 15px 100px;
    justify-content: center;
    align-items: center;
    border-radius: 10px;
    border: 1px solid #4945FF;
    background: #4945FF;
    color: #fff;
  }
  .main{

  }
  
  .footer{

  }
</style>