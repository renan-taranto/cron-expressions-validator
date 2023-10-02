<template>
  <article>
    <p>
      <span class="text__highlight">Cron Expressions</span> are used to create scheduled rules on AWS "EventBridge" (formerly called "Amazon CloudWatch Events").
      Many services like Lambda and ECS integrate with EventBridge to trigger actions like invoking functions and running scheduled tasks.
    </p>
    <p>
      <span class="text__highlight">The goal</span> of this web page is to help architects to validate their Cron Expressions.
      It can be useful while creating new rules, doing code reviews on "IaC" or just before applying any changes to the infrastructure.
      Insert the expression in the input and it will be validated.
    </p>
    <p>
      <span class="text__highlight">This web application</span> is an open source project authored by
      <a href="https://renantaranto.com/">Renan Taranto</a> and licensed by the MIT free software license.
    </p>
  </article>
</template>

<style scoped>
article {
  margin-top: 60px;
  text-align: justify;
  text-justify: inter-word;
}

@media (min-width: 768px) {
  article {
    display: flex;
    gap: 30px;
  }

  p {
    display: block;
    width: 33%;
  }
}
</style>
