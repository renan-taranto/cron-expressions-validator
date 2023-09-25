<script setup>
import AppInput from './AppInput.vue'
import {ref, watch} from 'vue'
import cron from 'cron-validate'

let isValid = ref(null)
const expression = ref('')

watch(expression, async(newExpression, oldExpression) => {
  if (newExpression !== oldExpression && newExpression !== '') {
    const cronResult = cron(newExpression, { preset: 'aws-cloud-watch' })
    isValid = cronResult.isValid()
  }
})
</script>

<template>
  <section>
    <section class="section__inputs">
      <AppInput :value="'15 10 ? * 6L 2019-2022'" class="input__sm"/>

      <AppInput :valus="'5,35'" :label="'Minutes'" class="input__md"/>
      <AppInput :value="'14'" :label="'Hours'" class="input__md"/>
      <AppInput :value="'*'" :label="'Day of month'" class="input__md"/>
      <AppInput :value="'*'" :label="'Month'" class="input__md"/>
      <AppInput :value="'?'" :label="'Day of week'" class="input__md"/>
      <AppInput :value="'*'" :label="'Year'" class="input__md"/>
    </section>
    <section class="section__write-out-expression">
      "At 22:00 on every day-of-week from Monday through Friday."
    </section>
  </section>
</template>

<style scoped>
.input__sm {
  width: 100%;
}

.input__md {
  display: none;
}

.section__write-out-expression {
  color: var(--color-grey);
  margin-top: 5px;
  text-align: center;
  font-size: .9rem;
  font-style: italic;
}

@media (min-width: 768px) {
  .section__inputs {
    display: flex;
    margin: 0 0 0 15%;
  }

  .input__sm {
    display: none;
  }

  .input__md {
    display: block;
    width: 16%;
    margin: 3px;
  }

  .section__write-out-expression {
    margin: 0 0 0 15%;
    text-align: right;
  }
}

@media (min-width: 992px) {
  .section__inputs {
    display: flex;
    margin: 0 0 0 15%;
  }

  .section__write-out-expression {
    margin-top: 10px;
  }
}

</style>
