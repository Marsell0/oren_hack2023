<script>
  import BlueButton from "../components/BlueButton.svelte";


import CompanyView from "../view/CompanyView.svelte";
import TestsView from "../view/TestsView.svelte";
import ResultView from "../view/ResultView.svelte";
import SupportView from"../view/SupportView.svelte";
import ApplicationView from "../view/ApplicationView.svelte";
import EducationView from "../view/EducationView.svelte";
import BaseTests from "../view/BaseTests.svelte";
import EmployeeView from "../view/EmployeeView.svelte";
import AnalView from "../view/AnalView.svelte";
import EducationBaseView from "../view/EducationBaseView.svelte";
  import { onMount } from "svelte";
  import axios from "axios";
let view = 'company'
let id = localStorage.getItem('token')
console.log(id);
var base64Url = id.split('.')[1];
var base64 = base64Url.replace(/-/g, '+').replace(/_/g, '/');
var jsonPayload = decodeURIComponent(window.atob(base64).split('').map(function(c) {
    return '%' + ('00' + c.charCodeAt(0).toString(16)).slice(-2);
}).join(''));

let url = 'http://xn--e1agmfegjgclf.xn----7sbpbfclakh1al9a7fxc.xn--p1ai:8000'
let token = JSON.parse(jsonPayload) 
localStorage.id = token['UserId']
let res = axios.get(url+"/portals/get_portal_by_owner_id", {
  headers:{
    'Authorization': localStorage.getItem('token').split(' ')[1]
  },
  params: {
    'owner_id': localStorage.getItem('id')
  }
})
console.log('get_portla');
console.log(res);
const userMenu = [
  {
    img: 'src/assets/sidebar/education.png',
    title: 'Моё обучение',
    id: 'education'
  },
  {
    img: 'src/assets/sidebar/test.png',
    title: 'Мои тесты',
    id: 'tests'
  },
  {
    img: 'src/assets/sidebar/result.png',
    title: 'Мои результаты',
    id: 'results'
  },
  {
    img: 'src/assets/sidebar/support.png',
    title: 'Мои обращения',
    id: 'support'
  },
]

const managerMenu = [
  {
    img: 'src/assets/sidebar/education.png',
    title: 'Моё обучение',
    id: 'education'
  },
  {
    img: 'src/assets/sidebar/test.png',
    title: 'Мои тесты',
    id: 'tests'
  },
  {
    img: 'src/assets/sidebar/result.png',
    title: 'Мои результаты',
    id: 'results'
  },
  {
    img: 'src/assets/sidebar/support.png',
    title: 'Мои обращения',
    id: 'support'
  },
  {
    img: 'src/assets/sidebar/application.png',
    title: 'Мои заявки',
    id: 'application'
  },
  {
    img: 'src/assets/sidebar/education.png',
    title: 'База учебных материалов',
    id: 'education_base'
  },
  {
    img: 'src/assets/sidebar/tests_base.png',
    title: 'База тестов',
    id: 'tests_base'
  },
  {
    img: 'src/assets/sidebar/employee.png',
    title: 'База сотрудников',
    id: 'employee'
  },
  {
    img: 'src/assets/sidebar/anal.png',
    title: 'Аналитика по компании',
    id: 'anal'
  },
]

const adminMenu =  [
  {
    img: 'src/assets/sidebar/education.png',
    title: 'Моё обучение',
    id: 'education'
  },
  {
    img: 'src/assets/sidebar/test.png',
    title: 'Мои тесты',
    id: 'tests'
  },
  {
    img: 'src/assets/sidebar/result.png',
    title: 'Мои результаты',
    id: 'results'
  },
  {
    img: 'src/assets/sidebar/support.png',
    title: 'Мои обращения',
    id: 'support'
  },
  {
    img: 'src/assets/sidebar/application.png',
    title: 'Мои заявки',
    id: 'application'
  },
  {
    img: 'src/assets/sidebar/education.png',
    title: 'База учебных материалов',
    id: 'education_base'
  },
  {
    img: 'src/assets/sidebar/tests_base.png',
    title: 'База тестов',
    id: 'tests_base'
  },
  {
    img: 'src/assets/sidebar/employee.png',
    title: 'База сотрудников',
    id: 'employee'
  },
  {
    img: 'src/assets/sidebar/anal.png',
    title: 'Аналитика по компании',
    id: 'anal'
  },
  {
    img: 'asd',
    title: 'Настройки',
    id: 'https://google.com',
  }
]


function changeChecked(id){
  let elem = document.getElementById(id)
  let removeElem = document.getElementsByClassName('_checked')[0]

  removeElem.classList.remove('_checked')
  elem.classList.add('_checked')

}
</script>

  <div class="profile">
    <div class="profile__sidebar">
      <div class="sidebar__header">
        <img src="" alt="" class="header__logo">
        <p class="header__text">Организация</p>
      </div>
      <div class="sidebar__menu">
      {#if localStorage.role === 'Common'}
        <div id="company" class="menu__list _checked" on:click={() => { view = 'company'; console.log(view); changeChecked('company');
        }}>
          <img src="src/assets/sidebar/company.png" alt="" class="list__img">
          <a class="list__item">Наша компания</a>
        </div> 
        {#each userMenu as { img, title, id}}
          <div id="{id}" class="menu__list" on:click={() => { view = id; console.log(view); changeChecked(id);
          }}>
            <img src="{img}" alt="" class="list__img">
            <a class="list__item">{title}</a>
          </div> 
        {/each}
      {:else if localStorage.role === 'Organization'}
        <div id="company" class="menu__list _checked" on:click={() => { view = 'company'; console.log(view); changeChecked('company');
        }}>
          <img src="src/assets/sidebar/company.png" alt="" class="list__img">
          <a class="list__item">Наша компания</a>
        </div> 
        {#each managerMenu as { img, title, id}}
          <div id="{id}" class="menu__list" on:click={() => { view = id; console.log(view); changeChecked(id);
          }}>
            <img src="{img}" alt="" class="list__img">
            <a class="list__item">{title}</a>
          </div> 
        {/each}
      {:else if localStorage.role === 'Administrator'}
        <div id="company" class="menu__list _checked" on:click={() => { view = 'company'; console.log(view); changeChecked('company');
        }}>
          <img src="src/assets/sidebar/company.png" alt="" class="list__img">
          <a class="list__item">Наша компания</a>
        </div> 
        {#each adminMenu as { img, title, id}}
          <div class="menu__list" on:click={() => { view = id; console.log(view); changeChecked(id);
          }}>
            <img src="{img}" alt="" class="list__img">
            <a class="list__item">{title}</a>
          </div> 
        {/each}
      {/if}
      </div>
    </div>
    <div class="profile__content">
      {#if view === 'company'}
        <CompanyView></CompanyView>
      {:else if view === 'education'}
        <EducationView {view}></EducationView>
      {:else if view === 'tests'}
        <TestsView {view}></TestsView>
      {:else if view === 'results'}
        <ResultView></ResultView>
      {:else if view === 'support'}
        <SupportView></SupportView>
      {:else if view === 'application'}
        <ApplicationView></ApplicationView>
      {:else if view === 'education_base'}
        <EducationBaseView {view}></EducationBaseView>
      {:else if view === 'tests_base'}
        <BaseTests {view}></BaseTests>
      {:else if view === 'employee'}
        <EmployeeView></EmployeeView>
      {:else if view === 'anal'}
        <AnalView></AnalView>
      {/if}
    </div>
  </div>

<style>
  .profile{
    display: flex;
    flex-direction: row;
    font-family: 'SF';
  }
  .profile__sidebar{
    border: 1px solid #F0F0FF;
    background: #FFF;
    min-height: 100%;

  }
  .sidebar__header{
    border: 1px solid #F0F0FF;
    background: #FFF;
  }
  .header__logo{

  }
  .header__text{

  }
  .sidebar__menu{
    display: flex;
    flex-direction: column;
  }
  .menu__list{
    display: flex;
    flex-direction: row;
    margin: 10px 10px;
    padding: 10px 10px;
    align-items: center;
    border: 1px solid #fff;
    transition: 0.3s ease all;
  }
  .menu__list:hover{
    cursor: pointer;
    background-color: #F6F6F9;
    transition: 0.3s ease all;
    border-radius: 5px;
    border: 1px solid #e7e7f1;
  }
  ._checked{
    border-radius: 5px;
    background:#F0F0FF;
  }
  .list__img{
    width: 18px;
    height: 18px
  }
  .list__item{
    padding: 0px 15px;
    color:#271FE0;
    text-decoration: none;
    font-feature-settings: 'clig' off, 'liga' off;

    font-size: 16px;
    font-style: normal;
    font-weight: 400;
    line-height: 16px; 
  }
  .profile__content{
    background-color: #F6F6F9;
    height: 100%;
    width: 100%;
    
  }

</style>