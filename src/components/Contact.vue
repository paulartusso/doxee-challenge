<template>
  <div class="contact-container">
    <div class="container">
      <div class="text-container">
        <span>
          Per qualsiasi tipo di <span>problema o dubbio </span><br />
          non esitare a <span>chiamare il nostro</span> <br /><span>
            Servizio Clienti.</span
          >
        </span>
      </div>
      <div class="button-container">
        <button>Chiama ora</button>
      </div>
      <div class="text-container" style="width: 90%">
        <span>
          Oppure da <span>telefono fisso</span> chiama il <br />
          numero <span>800 050 101</span>
        </span>
      </div>
    </div>
  </div>
</template>

<style scoped lang="scss">
.contact-container {
  display: flex;
  justify-content: center;
  align-items: center;
  flex-direction: column;
  width: 100%;
  background-color: #003478;
  padding-bottom: 20px;
  .bottom-div {
    width: 92%;
    //position: relative;
    background-color: #59ad96;
  }
  .container {
    //position: absolute;
    background-color: #85c8b5;
    //right: 21px;
    padding-bottom: 15px;
    width: 90%;
    // z-index: 1;
    .text-container {
      display: flex;
      flex-direction: column;
      justify-content: flex-start;
      align-items: center;
      margin-top: 20px;
    }
    span {
      font-size: 16px;
      line-height: 19px;
      color: #003478;
      span {
        font-weight: 600;
      }
    }
  }
  .button-container {
    display: flex;
    justify-content: center;
    align-items: center;
    button {
      padding: 15px;
      font-size: 18px;
      font-weight: 600;
      width: 87%;
      margin-top: 20px;
      color: #ffffff;
      background: #003478;
      border-radius: 20px;
      border: none;
    }
  }
}
</style>
