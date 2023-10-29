<script>
  import Education from "../components/Education.svelte";
  import BlueButton from "../components/BlueButton.svelte";
  import AddMaterialsModal from "../components/AddMaterialsModal.svelte"
  import axios from "axios";
  import { onMount } from "svelte";

  export let view
  let title = 'Название курса'
  let subtitle = 'Описание курса'
  let type = ''

  let modules
  let url = 'http://xn--e1agmfegjgclf.xn----7sbpbfclakh1al9a7fxc.xn--p1ai:8000'
  let res
  async function getModules(){
    res = await axios.get(url+"/tests/modules/get_all", {
      headers: {
        'Authorization': localStorage.getItem('token').split(' ')[1]
      }
    })
    console.log(localStorage.getItem('token').split(' ')[1]);
    
    modules = res['data']
    console.log(modules)
  }

  onMount(() => {
    getModules()
  })
</script>
  
  <div class="modules">
    <div class="modules__row">
      <Education {title} {subtitle} {view}></Education>
      <Education {title} {subtitle} {view}></Education>
      <Education {title} {subtitle} {view}></Education>
    </div>
    <div class="modules__row">
      <Education {title} {subtitle} {view}></Education>
      <Education {title} {subtitle} {view}></Education>
      <Education {title} {subtitle} {view}></Education>
    </div>
    <div class="modules__row">
      <Education {title} {subtitle} {view}></Education>
      <Education {title} {subtitle} {view}></Education>
      <Education {title} {subtitle} {view}></Education>
    </div>
    <!-- <div class="modules__add">
      <div class="add__btn">
        <button >Добавить</button>
      </div>
    </div> -->
    <AddMaterialsModal></AddMaterialsModal>
    <!-- <button on:click={getModules}>обновить</button> -->
  </div>
  
  <style>
    .modules{
      display: flex;
      flex-direction: column;
      margin: 0px auto;
      max-width: 1500px;
      min-height: 850px;
    }
    .modules__row{
      display: flex;
      flex-direction: row;
      justify-content: space-between;
      margin: 15px 0px;
    }
    .modules__add{
      margin: 0px 30px;
    }
    .add__btn{

    }
  </style>