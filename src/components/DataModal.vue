<script setup>
import Docs from "../assets/img/docs.png";
import Check from "../assets/img/check.png";
import Search from "../assets/img/search.png";
import CommonModal from "../components/CommonModal.vue";
import Contact from "../components/Contact.vue";
import DataFooter from "../components/DataFooter.vue";

defineProps({
  msg: {
    type: String,
    required: true,
  },
});
</script>
<script>
export default {
  data() {
    return {
      label1: "",
      label2: "",
      label3: "",
      ragioneSociale: "",
      partita: "",
      codice: "",
      checked: false,
      checkErrMsg: false,
      modalIsVisible: false,
      searchModal: false,
      closedModal: false,
      error: {
        errorInput1: false,
        errorInput2: false,
        errorInput3: false,
      },
    };
  },
  methods: {
    focusOnInput: function (label) {
      this[label] = "focused-input";
    },
    blurOnInput: function (label, input, errN) {
      this[label] = "";
      this.validarCampos(input, errN);
    },
    validarCampos: function (input, errN) {
      if (this[input].length <= 0) {
        this.error[errN] = true;
        console.log(this[input], this.error);
      } else {
        this.error[errN] = false;
      }
    },
    closeModal: function () {
      this.modalIsVisible = false;
      this.searchModal = false;
    },
    showCheck: function () {
      this.checked = !this.checked;
      console.log(this.checked);
    },
    showSearchModal: function () {
      this.searchModal = true;
    },
    showSuccessModal: function () {
      if (this.checked == false) {
        console.log(this.checked);
        this.checkErrMsg = true;
        console.log(this.checkErrMsg);
      } else if (
        this.ragioneSociale &&
        this.partita &&
        this.codice &&
        this.checked
      ) {
        this.checkErrMsg = false;
        this.error.errorInput1 = false;
        this.error.errorInput2 = false;
        this.error.errorInput3 = false;
        this.modalIsVisible = true;
        console.log(this.modalIsVisible);
      }
    },
  },
  computed: {
    input1Complete() {
      return this.ragioneSociale?.length > 0 ? "focused-input" : "";
    },
    input2Complete() {
      return this.partita?.length > 0 ? "focused-input" : "";
    },
    input3Complete() {
      return this.codice?.length > 0 ? "focused-input" : "";
    },
    getCheck() {
      return this.checked ? "showing-check" : "hidden-check";
    },
  },
};
</script>


<template>
  <div class="modal-container">
    <img :src="Docs" style="width: 60%" />
    <div class="modal">
      <span class="title">
        Titolare conto
        <img :src="Search" @click="showSearchModal()" />
      </span>
      <div class="relative">
        <span :class="`placeholder placeholder-1 ${label1} ${input1Complete}`">
          Ragione Sociale intestatario IBAN
        </span>
        <input
          v-model="ragioneSociale"
          type="text"
          class="data-input"
          @focus="focusOnInput('label1')"
          @blur="blurOnInput('label1', 'ragioneSociale', 'errorInput1')"
        />
      </div>
      <span v-show="error.errorInput1" class="error-msg"
        >Intestatario IBAN obbligatorio</span
      >
      <div class="relative">
        <span :class="`placeholder placeholder-2 ${label2} ${input2Complete}`">
          Partita Iva intestatario IBAN
        </span>
        <input
          v-model="partita"
          type="text"
          class="data-input"
          @focus="focusOnInput('label2')"
          @blur="blurOnInput('label2', 'partita', 'errorInput2')"
        />
      </div>
      <span v-if="error.errorInput2" class="error-msg"
        >Partita Iva intestatario IBAN obbligatorio</span
      >
      <div class="relative">
        <span :class="`placeholder placeholder-3 ${label3} ${input3Complete}`">
          Codice IBAN
        </span>
        <input
          v-model="codice"
          type="text"
          class="data-input"
          @focus="focusOnInput('label3')"
          @blur="blurOnInput('label3', 'codice', 'errorInput3')"
        />
      </div>
      <span v-if="error.errorInput3" class="error-msg"
        >Formato IBAN non corretto</span
      >

      <div class="checkbox-container">
        <div class="checkbox" @click="showCheck()">
          <img :src="Check" :class="`${getCheck}`" />
        </div>
        <span>
          ho letto e acconsento al trattamento dei dati <br />
          secondo le finalità espresse nell
          <span style="text-decoration: underline; color: #1b4175">
            'informativa <br />
            della privacy
          </span>
        </span>
      </div>
      <span v-if="checkErrMsg" class="error-msg">Consenso obligatorio</span>
      <div class="button-container" id="button-container">
        <button @click="showSuccessModal()">Invia i dati</button>
      </div>
    </div>
  </div>
  <Contact />
  <DataFooter />
  <CommonModal
    img="show"
    msg="Inserendo i dati richiesti, in base 
alle condizioni indicate nel contratto 
di fornitura sottoscritto, autorizza 
la società GAXA S.p.A. ad addebitare 
in via continuativa sul conto corrente identificato dal codice IBAN qui riportato, nella data di scadenza indicata 
dal Creditore, tutti gli addebiti diretti SEPA inviati dallo stesso Creditore."
    @close-modal="closeModal"
    v-if="searchModal"
  />
  <CommonModal
    msg="Abbiamo preso in carica la richiesta. Riceverai a breve una e-mail per firmarla con codice OTP. "
    @close-modal="closeModal"
    v-if="modalIsVisible"
  />
</template>

<style scoped lang="scss">
.modal-container {
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
  margin-top: 40px;
  padding-bottom: 25px;
  .modal {
    width: 92%;
    margin-top: -25px;
    display: flex;
    flex-direction: column;
    padding: 20px;
    background-color: #ffffff;
    border-radius: 8px;
    border: 1px solid #ffffff;
    box-shadow: 0px 0px 20px 2px rgba(0, 0, 0, 0.45);
    .title {
      color: #003478;
      display: flex;
      justify-content: flex-start;
      align-items: center;
      font-weight: 600;
      img {
        width: 20px;
        margin-left: 8px;
      }
    }
    .relative {
      position: relative;
      width: 100%;
    }
    .placeholder {
      position: absolute;
      color: #575653;
      font-weight: 400;
      font-size: 12px;
      line-height: 14px;
      background: #ffffff;
      transition: all 0.2s linear;
      //z-index: 1;
      top: 35px;
      left: 15px;
    }
    .focused-input {
      top: 15px;
      z-index: 1;
    }
    .error-msg {
      font-size: 12px;
      color: #c3240b;
    }
    .err {
      border: 1px solid #c3240b;
    }
    .data-input {
      width: 100%;
      margin-top: 20px;
      background: transparent;
      border: 1px solid #003478;
      border-radius: 5px;
      height: 40px;
      padding-left: 10px;
    }
    .checkbox-container {
      display: flex;
      flex-direction: row;
      align-items: flex-start;
      justify-content: space-between;
      width: 85%;
      margin-top: 20px;
      .checkbox {
        border: 1px solid #003478;
        width: 20px;
        height: 20px;
        .hidden-check {
          display: none;
        }
        .showing-check {
          width: 16px;
          display: block;
        }
      }
      span {
        font-weight: 400;
        font-size: 12px;
        line-height: 14px;
        color: #575653;
      }
    }
    .button-container {
      display: flex;
      justify-content: center;
      align-items: center;
      button {
        padding: 13px;
        font-size: 18px;
        font-weight: 600;
        width: 85%;
        margin-top: 20px;
        color: #ffffff;
        background: #003478;
        border-radius: 10px;
        border: none;
      }
    }
  }
}

@media (min-width: 1024px) {
  .greetings h1,
  .greetings h3 {
    text-align: left;
  }
}
</style>
