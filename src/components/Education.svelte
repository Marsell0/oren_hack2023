<script>
// export let imgUrl
export let title
export let subtitle
export let view
// export let link
</script>

{#if view === 'education_base' && localStorage.role === 'Organization'}
  <div class="education">
    <div class="education__wrapper">
      <div class="education__logo">
        <img src="" alt="" class="logo__img">
      </div>
      <div class="education__text">
        <p class="text__title">{title}</p>
        <p class="text__subtitle">{subtitle}</p>
      </div>
      <div class="education__more">
        <div class="more__del">
          <p class="del__text">Удалить</p>
        </div>
        <div class="more__redact">
          <div class="redact__btn">
            <img src="/src/assets/education/edit.svg" alt="edit" class="btn__img">
            <p class="redact__text">Изменить</p>
          </div>
        </div>
      </div>
    </div>
  </div>
{:else}
  <div class="education">
    <div class="education__wrapper">
      <div class="education__logo">
        <img src="" alt="" class="logo__img">
      </div>
      <div class="education__text">
        <p class="text__title">{title}</p>
        <p class="text__subtitle">{subtitle}</p>
      </div>
      <div class="education__more">
        <div class="more__btn">
          <img src="/src/assets/education/external.svg" alt="" class="btn__img">
          <p class="btn__text">Больше</p>
        </div>
      </div>
    </div>
  </div>
{/if}


<style>
  .education{
    font-family: 'SF';
    border-radius: 4px;
    border: 0.5px solid var(--light-mode-neutral-150, #EAEAEF);
    background: var(--light-mode-neutral-0, #FFF);
    max-height: 230px;
    max-width: 410px;
    width: 20%;

    /* Table shadow */
    box-shadow: 0px 1px 4px 0px rgba(33, 33, 52, 0.10);
  }
  .education__wrapper{
    padding: 15px 10px;
    display: flex;
    flex-direction: column;
  }
  .education__logo{
    margin-bottom: 5%;
  }
  .logo__img{
    height: 64px;
    width: 64px;
    background-color: black;
  }
  .education__text{

  }
  .text__title{
    color: #212134;
    font-size: 16px;
font-style: normal;
font-weight: 500;
line-height: 20px; /* 125% */
  }
  .text__subtitle{
    color:#666687;
font-size: 14px;
font-style: normal;
font-weight: 400;
line-height: 20px; /* 142.857% */
  }
  .education__more{
    display: flex;
    justify-content: flex-end;
  }
  .more__del{
    display: flex;
    flex-direction: row;
    border-radius: 4px;
    background: var(--light-mode-danger-100, #FCECEA);
    transition: 0.3s ease all;
  }
  .more__del:hover{
    transition: 0.3s ease all;
    color: #FCECEA;
    background-color: #D02B20;
    cursor: pointer;
  }
  .more__del:hover > p{
    transition: 0.3s ease all;
    color: #FCECEA;
  }
  .del__text{
    padding: 10px 16px;
    color: #D02B20;
    font-size: 14px;
    font-style: normal;
    font-weight: 600;
    line-height: 16px; /* 114.286% */
  }
  .more__redact{
    display: flex;
    flex-direction: row;
    border-radius: 4px;
    border: 1px solid var(--light-mode-primary-200, #D9D8FF);
    background: var(--light-mode-primary-100, #F0F0FF);
    align-items: center;
    transition: 0.3s ease all;
    cursor: pointer;
    margin-left: 5px;
  }
  .more__redact:hover{
    background-color: #FFF;
    transition: 0.3s ease all;
  }
  .redact__btn{
    padding: 10px 14px;
    display: flex;
    flex-direction: row;
    align-items: center;
    
  }
  .redact__text{
    color: #4945FF;
    font-size: 14px;
    font-style: normal;
    font-weight: 600;
    line-height: 16px; /* 114.286% */
    padding-left: 5px;
  }
  .more__btn{
    /* display: flex;
    flex-direction: row;
    justify-content: flex-end;
    border-radius: 4px;
    border: 1px solid #DCDCE4;
    background:  #FFF; */
    display: inline-flex;
padding: 10px 16px;
justify-content: center;
align-items: center;
gap: 8px;
border-radius: 4px;
border: 1px solid var(--light-mode-neutral-200, #DCDCE4);
background: var(--light-mode-neutral-0, #FFF);
  }
  .btn__img{

  }
  .btn__text{
    color: #32324D;
text-align: right;

font-size: 14px;
font-style: normal;
font-weight: 600;
line-height: 16px; /* 114.286% */
  }
</style>