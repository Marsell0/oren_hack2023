<script>
import Input from "../components/Input.svelte";
import axios from "axios";
import { onMount } from "svelte";

let url = 'http://xn--e1agmfegjgclf.xn----7sbpbfclakh1al9a7fxc.xn--p1ai:8000'

let res, token
let name = "инфа", address, inn, phone_number, email, fio = "Неизвестный", mission, purpose
async function getProfile(){
  token = localStorage.getItem('token').split(' ')
  console.log(token[1]);
  res = await axios.get(url+"/users/profile", {
    headers:{
      'Authorization': token[1]
    },
    params: {
      'owner_id': localStorage.id
    }
  }).then(() => {
    console.log(res);
    email = res['data']['email']
    phone_number = res['data']['phone_number']
    address = res['data']['address']
    name = res['data']['name']
    fio = res['data']['fio']
    purpose = res['data']['purpose']
    mission = res['data']['mission']
    console.log(name);
  })
  console.log(res);
  console.log(res[1]);
  
}

onMount(() => {
  getProfile()
})
</script>

<div class="company">
  <div class="company__wrapper">
    <div class="company__header">
      <div class="header__wrapper">
        <div class="header__color">
        
        </div>
        <div class="header__desc">
          <div class="desc__desc">
            <div class="desc__logo">
  
            </div>
            <div>
              <p class="desc__title">Название компании</p>
            </div>
          </div>

          <div class="header__upload">
            Загрузить иконку
          </div>
        </div>

      </div>
    </div>
    <div class="company__body">
      <div class="body__wrapper">
        <div class="body__info">
          <div class="info__text">Информация</div>
          <div class="info__input">
            <div class="input__row">
              <div class="row__block">
                <p class="block__text">Название компании</p>
                {#if localStorage.role === 'Organization'}
                  <input class="input" type="text" value="{name}">
                {:else}
                  <input disabled class="input" type="text" value="{name}">
                {/if}
              </div>
            </div>
            <div class="input__row">
              <div class="row__block">
                <p class="block__text">Цель</p>
                {#if localStorage.role === 'Organization'}
                  <input class="input" type="text" value="{purpose}">
                {:else}
                  <input disabled class="input" type="text" value="{purpose}">
                {/if}
              </div>
              <div class="row__block">
                <p class="block__text">Миссия</p>
                {#if localStorage.role === 'Organization'}
                  <input class="input" type="text" value="{mission}">
                {:else}
                  <input disabled class="input" type="text" value="{mission}">
                {/if}
              </div>
            </div>
            <div class="input__row">
              <div class="row__block">
                <p class="block__text">Фактический адрес</p>
                {#if localStorage.role === 'Organization'}
                  <input class="input" type="text" value="{address}">
                {:else}
                  <input disabled class="input" type="text" value="{address}">
                {/if}
              </div>
              <div class="row__block">
                <p class="block__text">ИНН</p>
                {#if localStorage.role === 'Organization'}
                  <input class="input" type="text" value="{inn}">
                {:else}
                  <input disabled class="input" type="text" value="{inn}">
                {/if}
              </div>
            </div>
          </div>
        </div>
        <div class="body__contact">
          <div class="info__text">Контакты</div>
          <div class="info__input">
            <div class="input__row">
              <div class="row__block">
                <p class="block__text">Телефон</p>
                {#if localStorage.role === 'Organization'}
                  <input class="input" type="text" value="{phone_number}">
                {:else}
                  <input disabled class="input" type="text" value="{phone_number}">
                {/if}
              </div>
              <div class="row__block">
                <p class="block__text">E-mail</p>
                {#if localStorage.role === 'Organization'}
                  <input class="input" type="text" value="{name}">
                {:else}
                  <input disabled class="input" type="text" value="{name}">
                {/if}
              </div>
              <div class="row__block">
                <p class="block__text">Представитель</p>
                <Input {name} />
              </div>
            </div>
          </div>
        </div>
      </div>
    </div>
  </div>
</div>

<style>
  .company{
    margin: 0% 15%;
    min-height: 850px;
    font-family: 'SF';
  }
  .company__wrapper{
    margin-top: 15px;
    display: flex;
    flex-direction: column;
  }
  .company__header{

  }
  .header__wrapper{

  }
  .header__color{
    background-color: #4945FF;
    height: 100px;
    width: 100%;
  }
  .header__desc{
    display: flex;
    padding: 3% 2%;
    flex-direction: row;
    background-color: #FFF;
    align-items: center;
    justify-content: space-between;
  }
  .desc__desc{
    display: flex;
    flex-direction: row;
    align-items: center;
  }
  .desc__logo{
    background-color: #4945FF;
    width: 64px;
    height: 64px;

  }
  .desc__title{
    padding: 0px 5px;
    color: var(--light-mode-primary-600, #4945FF);
    text-align: center;
    font-feature-settings: 'clig' off, 'liga' off;
    font-family: 'SF';
    font-size: 25px;
    font-style: normal;
    font-weight: 600;
    line-height: 22px; /* 88% */
  }
  .header__upload{
    display: inline-flex;
padding: 10px 16px;
justify-content: center;
align-items: center;
gap: 8px;
border-radius: 4px;
border: 1px solid var(--light-mode-primary-200, #D9D8FF);
background: var(--light-mode-primary-100, #F0F0FF);
  }


  .company__body{
    margin-top: 80px;
    border-radius: 4px;
    border: 0.5px solid #EAEAEF;
    background: #FFF;
    box-shadow: 0px 1px 4px 0px rgba(33, 33, 52, 0.10);
  }
  .body__wrapper{
    padding: 2% 3%;
  }
  .body__info{

  }
  .info__text{
    color: #212134;
    font-feature-settings: 'clig' off, 'liga' off;
    padding-bottom: 2%;

    /* Delta - H3 */
    font-family: 'SF';
    font-size: 16px;
    font-style: normal;
    font-weight: 500;
    line-height: 20px; /* 125% */

  }
  .info__input{
    display: flex;
    flex-direction: column;
    flex-wrap: wrap;
  }
  .input__row{
    display: flex;
    flex-direction: row;
    margin-bottom: 25px;
  }
  .row__block{
    margin-right: 25px;
  }
  .block__text{
    color: var(--light-mode-neutral-800, #32324D);
font-feature-settings: 'clig' off, 'liga' off;

/* Pi (Bold) - Small button text */
font-size: 12px;
font-style: normal;
font-weight: 600;
line-height: 16px; /* 133.333% */
  }

</style>