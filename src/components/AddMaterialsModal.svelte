<script>
  import axios from "axios";
  let name, portal_id, url_file
  let url = 'http://xn--e1agmfegjgclf.xn----7sbpbfclakh1al9a7fxc.xn--p1ai:8000'

  let res, token, tok, params
  token = localStorage.getItem('token').split(' ')
  async function createModule(){
    console.log(localStorage.getItem('id'));  
    tok = token[1]
    params =       {
        'name': name,
        'portal_id': localStorage.getItem('id'),
        'url_file': null
      }
    console.log(tok);
    res = await axios.post(url+"/tests/modules/create", params, {
      headers: {
        'Authorization': tok
      }
    })
    console.log(res);
  }
</script>

<div class="modal">
  <div class="modal__wrapper">
    <form  class="modal__form">
      <div class="form__block">
        <p class="block__text">name</p>
        <input type="text" bind:value={name} class="block__input">
      </div>
      <div class="form__block">
        <p class="block__text">name</p>
        <input type="text" class="block__input">
      </div>
      <div class="form__block">
        <p class="block__text">link</p>
        <input type="text" bind:value={url_file} class="block__input">
      </div>
      <div class="form__block">
        <div class="block__remove"></div>
        <input class="block__save" type="text" on:click={createModule} value="Сохранить">
      </div>
    </form>
  </div>
</div>

<style>
  /* .modal{
    width: 500px;
    height: 200px;
    position: fixed;
    top: 0;
    bottom: 0;
    right: 0;
    left: 0;
    display: flex;
    justify-content: center;
    align-items: center;
    background-color: black;
  } */
</style>