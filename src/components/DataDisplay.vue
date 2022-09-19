<script setup>
defineProps({
  title: {
    type: String,
    required: true,
  },
  data: {
    type: String,
    required: true,
  },
});
</script>

<template>
  <div class="data-container">
    <h3>
      {{ title }}
    </h3>
    <span class="data">
      {{ data }}
    </span>
  </div>
</template>

<style scoped lang="scss">
.data-container {
  display: flex;
  align-items: flex-start;
  justify-content: center;
  flex-direction: column;
  h3 {
    font-family: "Work Sans", sans-serif;
    color: #ffffff;
    text-align: left;
    font-size: 14px;
    margin-top: 15px;
  }
  .data {
    font-size: 18px;
    text-align: left;
    line-height: 21px;
    letter-spacing: 0.3px;
    font-weight: 700;
    color: #ffffff;
  }
}

@media (min-width: 1024px) {
}
</style>

