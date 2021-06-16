<template>
  <div class="card">
    <div class="card-container">
      <img :src="item.poster" alt="">
    </div>
    <div class="text-container">
      <h2>{{ item.title }}</h2>
      <div>
      <p>{{ item.author }}</p>
      <p>{{ item.year }}</p>
      </div>
    </div>
  </div>
</template>

<script>
export default {
    name: "Card",
    props: [ "item" ]
}
</script>

<style scoped>

  .card {
    display: flex;
    flex-direction: column;
    align-items: center;
    height: 90%;
    width: 82%;
    margin: auto;
    background-color: #2e3a46;
  }

  img {
    width: 100%;
    height: 100%;
  }

  .card-container {
    height: 157px;
  }

  .text-container {
    display: flex;
    flex-direction: column;
    justify-content: space-between;
    height: 167px;
    align-items: center;
}

  h2 {
    color: white;
    font-size: 24px;
    margin: 15px 0;
    text-align: center;
  }

  p {
    color: #747d76;
    font-size: 16px;
    text-align: center;
  }

</style>