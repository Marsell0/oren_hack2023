<script>
import Input from "../components/Input.svelte";

let name = 'Инфа'
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
            <Input {name} /> 
            <Input {name} />
            <Input {name} />
            <Input {name} />
          </div>
        </div>
        <div class="body__contact">
          <div class="info__text">Контакты</div>
          <div class="info__input">
            <Input {name} /> 
            <Input {name} />
            <Input {name} />
          </div>
        </div>
      </div>
    </div>
  </div>
</div>

<style>
  .company{
    margin: 0% 15%;
  }
  .company__wrapper{
    margin-top: 100px;
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

  }
  .body__info{

  }
  .info__text{
    color: #212134;
    font-feature-settings: 'clig' off, 'liga' off;
    padding: 2% 2%;

    /* Delta - H3 */
    font-family: 'SF';
    font-size: 16px;
    font-style: normal;
    font-weight: 500;
    line-height: 20px; /* 125% */

  }
  .info__input{
    display: flex;
    flex-direction: row;
    flex-wrap: wrap;
  }

</style>