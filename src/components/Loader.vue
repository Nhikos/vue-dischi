<template>
  <div class="loader">
      <div class="text">
          <h2> {{ message }} </h2>
      </div>
  </div>
</template>

<script>
export default {
    name: "Loader",
    props: ["message"]
}
</script>

<style>
    .loader {
        display: flex;
        justify-content: center;
        align-content: center;
        height: calc(100vh - 70px);
    }

    .text {
        display: flex;
        flex-direction: column;
        justify-content: center;
        align-content: center;
        width: 100%;
    }

    h2 {
        color: blue;
        text-align: center;
    }
</style>