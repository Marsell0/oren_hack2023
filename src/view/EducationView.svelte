<script>
  import Education from "../components/Education.svelte";
  
  export let view
  let title = 'Название курса'
  let subtitle = 'Описание курса'
  
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
  </div>
  
  <style>
    .modules{
      display: flex;
      flex-direction: column;
      margin: 0px auto;
      min-height: 850px;
    }
    .modules__row{
      display: flex;
      flex-direction: row;
      justify-content: space-around;
      margin: 15px 0px;
    }
  </style>