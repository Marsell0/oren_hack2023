<script>
  export let type

  let hovering
  function enter(){
    hovering = true
  }
  function leave(){
    hovering = false
  }
</script>

<button class="button" type="{type}" on:mouseenter={enter} on:mouseleave={leave}>
  <slot class="button__text" {hovering}></slot>
  <p class="button__text" style="display: none;"></p>
</button>

<style scoped>
  .button{
    display: inline-flex;
    padding: 10px 50px;
    justify-content: center;
    align-items: center;
    border-radius: 10px;
    border: 1px solid  #271FE0;
    color: #271FE0;
    box-shadow: 0px 1px 2px 0px rgba(198, 228, 246, 0.05);
    transition: all ease 0.5s;
  }
  .button:hover{
    transition: all ease 0.5s;
    border-radius: 10px;
    border: 1px solid #F0F0FF;
    background: #F0F0FF;
    cursor: pointer;
  }
  .button__text{
    color: blue
  }
  
</style>