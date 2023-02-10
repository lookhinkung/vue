<template>
  <div class="about">
    <h1>This is an about page</h1>
  </div>
</template>

<style>
  .about {
    min-height: 100vh;
    display: flex;
    align-items: center;
    justify-content: center;
    background-color: #F0F0F0;
  }

  h1 {
    font-size: 48px;
    font-weight: bold;
    color: #333;
  }

  @media (min-width: 1024px) {
    .about {
      padding: 50px;
    }
  }
</style>