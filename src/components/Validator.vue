<script setup lang="ts">
import AppInput from './AppInput.vue'
import {ref, reactive, watch} from 'vue'
import cron from 'cron-validate'

interface Expression {
  minutes?: String,
  hours?: String,
  dayOfMonth?: String,
  month?: String,
  dayOfWeek?: String,
  year?: String
}
const expression: Expression = reactive({
  minutes: '15,35',
  hours: '14',
  dayOfMonth: '*',
  month: '*',
  dayOfWeek: '?',
  year: '*'
})

const isValid = ref<Boolean>(true)
watch(expression, async(newExpression) => {
    const cronResult = cron(
        `${newExpression.minutes} ${newExpression.hours} ${newExpression.dayOfMonth} ${newExpression.month} ${newExpression.dayOfWeek} ${newExpression.year}`,
        { preset: 'aws-cloud-watch' }
    )
    isValid.value = cronResult.isValid()
})
</script>

<template>
  <section>
    <section class="section__inputs">
      <AppInput :value="'15 10 ? * 6L 2019-2022'" class="input__sm"/>

      <AppInput v-model="expression.minutes" label="Minutes" class="input__md"/>
      <AppInput v-model="expression.hours" label="Hours" class="input__md"/>
      <AppInput v-model="expression.dayOfMonth" label="Day of month" class="input__md"/>
      <AppInput v-model="expression.month" label="Month" class="input__md"/>
      <AppInput v-model="expression.dayOfWeek" label="Day of week" class="input__md"/>
      <AppInput v-model="expression.year" label="Year" class="input__md"/>
    </section>
    <section class="section__result">
      This expression is <span class="text__bold">{{ isValid ? '' : 'not' }} valid</span>.
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

.section__result {
  color: var(--color-orange);
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

  .section__result {
    margin: 0 0 0 15%;
    text-align: right;
  }
}

@media (min-width: 992px) {
  .section__inputs {
    display: flex;
    margin: 0 0 0 15%;
  }

  .section__result {
    margin-top: 10px;
  }
}

</style>
