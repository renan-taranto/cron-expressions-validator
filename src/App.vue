<script setup>
import Title from './components/Title.vue'
import Validator from './components/Validator.vue'
import Instructions from './components/Instructions.vue'
</script>

<template>
  <main>
    <Title class="title"/>
    <Validator class="validator"/>
  </main>
  <Instructions class="instructions"/>
</template>

<style scoped>
.validator {
  margin-top: 40px;
}

@media (min-width: 768px) {
  main {
    width: 100%;
    display: flex;
    align-items: center;
    justify-content: space-between;
  }

  .title {
    width: 50%;
  }
  .validator {
    width: 50%;
    margin: 0;
  }

  .instructions {
    margin-top: 70px;
  }
}

@media (min-width: 992px) {
  .title {
    width: 35%;
  }
  .validator {
    width: 65%;
  }
}

@media (min-width: 1400px) {
  .title {
    width: 45%;
  }
  .validator {
    width: 55%;
  }
}
</style>
