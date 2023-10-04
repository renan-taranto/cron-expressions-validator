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
const expressionParts: Expression = reactive({
  minutes: '15,35',
  hours: '14',
  dayOfMonth: '*',
  month: '*',
  dayOfWeek: '?',
  year: '*'
})
const fullExpression = ref<String>('15,35 14 * * ? *')
const isValid = ref<Boolean>(true)

watch(expressionParts, async(newExpressionParts) => {
    validateExpression(`${newExpressionParts.minutes} ${newExpressionParts.hours} ${newExpressionParts.dayOfMonth} ${newExpressionParts.month} ${newExpressionParts.dayOfWeek} ${newExpressionParts.year}`)
})
watch(fullExpression, async(newExpression) => {
    validateExpression(newExpression)
})

const validateExpression = (expression: String) => {
  const cronResult = cron(expression, { preset: 'aws-cloud-watch' })
  isValid.value = cronResult.isValid()
}

</script>

<template>
  <section>
    <section class="section__inputs">
      <AppInput v-model="fullExpression" class="input__sm"/>

      <AppInput v-model="expressionParts.minutes" label="Minutes" class="input__md"/>
      <AppInput v-model="expressionParts.hours" label="Hours" class="input__md"/>
      <AppInput v-model="expressionParts.dayOfMonth" label="Day of month" class="input__md"/>
      <AppInput v-model="expressionParts.month" label="Month" class="input__md"/>
      <AppInput v-model="expressionParts.dayOfWeek" label="Day of week" class="input__md"/>
      <AppInput v-model="expressionParts.year" label="Year" class="input__md"/>
    </section>
    <section class="section__result">
      <span v-if="isValid">
        <span class="text--bold color--primary">Valid</span> expression.
      </span>
      <span v-else>
        This expression is <span class="text--bold color--primary">Not Valid</span>.
      </span>
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
