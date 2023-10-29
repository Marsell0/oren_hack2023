<script>
  import Education from "../components/Education.svelte";
  import BlueButton from "../components/BlueButton.svelte";
  
  export let view
  let title = 'Название курса'
  let subtitle = 'Описание курса'
  let type = ''
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
    <div class="modules__add">
      <div class="add__btn">
        <BlueButton {type}>Добавить</BlueButton>
      </div>
    </div>
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