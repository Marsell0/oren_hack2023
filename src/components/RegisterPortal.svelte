<script>
  import axios from "axios";

  let login, password, name, phone_number, inn, address
  let res, params
  let isError = false
  let url = 'http://xn--e1agmfegjgclf.xn----7sbpbfclakh1al9a7fxc.xn--p1ai:8000'

  async function createPortal(){
    console.log('start createPortal');
    params = {
      'email': login,
      'password': password,
      'name': name,
      'phone_number': phone_number,
      'inn': inn,
      'address': address
    }
    res = await axios.post(url+'/portals/create', params, {
      headers: {
        'Content-Type': 'application/json'
      }
    })
    localStorage.role = 'Organization'
    console.log(res['data']);
    localStorage.id = res['data']['owner_id']
    console.log('finish createPortal');
  }

</script>

<div class="reg">
  <div class="reg__wrapper">
    <p class="reg__title">Регистрация</p>
    <form on:submit|preventDefault={createPortal} action="" class="reg__form">
      <input class="form__input" type="text" bind:value={login} placeholder="E-mail">
      <input type="password" bind:value={password} class="form__input" placeholder="Пароль">
      <input class="form__input" type="text" bind:value={name} placeholder="Название организации">
      <input class="form__input" type="text" bind:value={phone_number} placeholder="Контактный телефон">
      <input class="form__input" type="text" bind:value={inn} placeholder="ИНН">
      <input class="form__input" type="text" bind:value={address} placeholder="Фактический адрес">
      <div style="display: flex; justify-content: center;">
        <input type="submit" class="form__btn" value="Зарегистрироваться">
      </div>
      
      {#if isError}
        <p>{res}</p>
      {/if}
    </form>
  </div>
  
</div>

<style>
  .reg{
    display: flex;
    flex-direction: column;
    margin: 0px auto;
    max-width: 590px;
    border-radius: 35px;
    border: 1px solid #DCDCE4;
    background: #FFF;
    font-family: 'SF';
  }
  .reg__wrapper{
    padding: 70px 90px;
  }
  .reg__title{
    color: var(--light-mode-primary-700, #271FE0);
    font-feature-settings: 'clig' off, 'liga' off;
    margin-bottom: 20%;

    /* H1 */
    font-size: 32px;
    font-style: normal;
    font-weight: 600;
    line-height: 40px; /* 125% */
  }
  .reg__form{
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
</style>
