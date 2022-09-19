<script setup>
import Docs from "../assets/img/docs.png";
import Check from "../assets/img/check.png";
import Search from "../assets/img/search.png";
import Close from "../assets/img/close-button.png";

import Success from "../assets/img/success.png";

defineProps({
  msg: {
    type: String,
    required: true,
  },
  img: {
    type: String,
    required: false,
  },
});
</script>
<script>
export default {
  data() {
    return {};
  },
  methods: {
    closeModal: function () {
      this.$emit("closeModal");
    },
  },
  computed: {
    hiddenModal() {
      return this.closedModal ? "hidden-overlay" : "";
    },
  },
};
</script>

<template>
  <div :class="`overlay ${hiddenModal}`">
    <div class="modal">
      <div class="close-button-container">
        <img :src="Close" @click="closeModal" />
      </div>
      <div class="msg-img-container">
        <span class="msg-container">
          {{ msg }}
        </span>
        <img v-if="img == show" :src="Success" style="width: 45px" />
      </div>
    </div>
  </div>
</template>

<style scoped lang="scss">
.hidden-overlay {
  display: none;
}
.overlay {
  position: fixed; /* Sit on top of the page content */
  width: 100vw; /* Full width (cover the whole page) */
  height: 100vh; /* Full height (cover the whole page) */
  top: 0;
  left: 0;
  right: 0;
  bottom: 0;
  background-color: rgba(0, 0, 0, 0.5); /* Black background with opacity */
  z-index: 2; /* Specify a stack order in case you're using a different order for other elements */
  cursor: pointer;
  display: flex;
  justify-content: center;
  align-items: center;
  .modal {
    background-color: #ffffff;
    width: 90%;
    box-shadow: 0px -4px 10px rgba(0, 0, 0, 0.25);
    border-radius: 10px;
    padding: 30px;
    text-align: center;
    font-size: 18px;
    line-height: 21px;
    text-align: center;
    color: #003478;
    .close-button-container {
      display: flex;
      justify-content: flex-end;
      align-items: center;
      img {
        width: 25px;
      }
    }
    .msg-img-container {
      display: flex;
      justify-content: center;
      align-items: center;
      flex-direction: column;
      .msg-container {
        margin-top: 20px;
      }
      img {
        width: 55px;
        margin-top: 15px;
      }
    }
  }
}
</style>