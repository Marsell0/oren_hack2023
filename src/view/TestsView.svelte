<script>

</script>

  <div class="tests">
    <div class="not_found">
      <img class="tests__not" src="/src/assets/404.svg" alt="">
      <p class="tests__not-text">Упс, ничего не найдено...</p>
    </div>
    
  </div>

<style>
  .tests{
    width: 100%;
    height: 100%;
  }
  .not_found{
    display: flex;
    flex-direction: column;
    align-items: center;
    margin: 10% 3%;
    padding: 10% 3%; 
  }
  .tests__not{
  }
  .tests__not-text{
    color: var(--light-mode-neutral-600, #666687);
text-align: center;
font-feature-settings: 'clig' off, 'liga' off;

/* Delta - H3 */
font-family: SF Pro Display;
font-size: 16px;
font-style: normal;
font-weight: 500;
line-height: 20px; /* 125% */
  }
</style>