<script>
  import axios from "axios";
  import Input from "./Input.svelte";
  let name, portal_id, url_file
  let url = 'http://xn--e1agmfegjgclf.xn----7sbpbfclakh1al9a7fxc.xn--p1ai:8000'

  let res, token, tok, params
  token = localStorage.getItem('token').split(' ')
  async function createModule(){
    console.log(localStorage.getItem('id'));  
    tok = token[1]
    params =       {
        'portal_id': localStorage.getItem('portal_id'),
        'name': name,
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
  .modal{

  }
  .modal__wrapper{

  }
  .modal__form{

  }
  .form__block{

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