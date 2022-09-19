<script setup>
//se importan los componentes
import DataModal from "./components/DataModal.vue";
import WelcomeText from "./components/WelcomeText.vue";
import DataDisplay from "./components/DataDisplay.vue";
import Logo from "./assets/img/logo-gaxa.png";
</script>

<template>
  <!--Acac html-->
  <div class="header-container">
    <header class="header">
      <img
        :src="Logo"
        alt="Gaxa-Logo"
        style="width: 50%; margin-top: 20px; margin-bottom: 20px"
      />
      <div>
        <h2>Attiva la Domiciliazione bancaria.</h2>
        <p>
          Così la bolletta non sarà più un pensiero! <br />
          Inserisci qui sotto il tuo Iban e il nome <br />
          dell’intestatario del conto.
        </p>
      </div>
    </header>

    <main class="content-container">
      <div class="columns-div">
        <h2>Titolare della fornitura</h2>
        <DataDisplay
          title="Cognome e Nome/Ragione sociale"
          data="Rossi Mario"
        />
        <DataDisplay title="Codice Fiscale/P.I." data="RSSMRA00A01H501C" />
        <DataDisplay
          title="Indirizzo della fornitura"
          data="Via tal dei tali 2, 12345, Roma (RO)"
        />
      </div>
      <div class="rows-div-container">
        <div class="rows-div">
          <DataDisplay title="Codice PDR" data="123456" />
          <DataDisplay title="Codice Cliente" data="1234567" />
        </div>
      </div>
    </main>

    <DataModal />
  </div>
</template>

<style scoped lang="scss">
header {
  line-height: 1.5;
}

.header-container {
  background-color: #003478;
}
.header {
  display: flex;
  justify-content: center;
  align-items: center;
  flex-direction: column;
  padding-top: 25px;
  div {
    display: flex;
    justify-content: center;
    align-items: flex-start;
    flex-direction: column;
    width: 80%;
    p {
      font-family: "Work Sans", sans-serif;
      color: #ffffff;
      text-align: left;
      font-size: 14px;
      margin-top: 5px;
    }
  }
}

.content-container {
  display: flex;
  justify-content: center;
  align-items: center;
  flex-direction: column;
  .columns-div {
    display: flex;
    justify-content: center;
    align-items: flex-start;
    flex-direction: column;
    width: 80%;
  }
  .rows-div-container {
    display: flex;
    justify-content: space-between;
    align-items: flex-start;
    width: 80%;
    .rows-div {
      display: flex;
      justify-content: space-between;
      flex-direction: row;
      width: 80%;
    }
  }
}
h2 {
  font-size: 18px;
  line-height: 21px;
  letter-spacing: 0.3px;
  font-weight: 700;
  color: #ffffff;
  margin-top: 30px;
  margin-bottom: 10px;
}

.logo {
  display: block;
  //margin: 0 auto 2rem;
}

@media (min-width: 1024px) {
  header {
    display: flex;
  }

  .logo {
    margin: 0 2rem 0 0;
  }
}
</style>
