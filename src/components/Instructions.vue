<template>
  <article>
    <p>
      <span class="text__highlight">Cron Expressions</span> are used for scheduled rules on AWS "EventBridge" (formerly called "Amazon CloudWatch Events").
      Currently, the only way to validate these on AWS is trough the Console, while creating or editing existing rules.
      This can be cumbersome when using "Infrastructure as Code" tools since you are not always logged to the AWS Console.
    </p>
    <p>
      <span class="text__highlight">The goal</span> of this web page is to help architects to validate Cron Expressions easier while doing code reviews on IaC or just
      before applying any changes to the infrastructure. Insert the expression in the input and it will be validated.
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
