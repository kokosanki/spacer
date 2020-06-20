<template>
    <div class="claimWrapper">
        <p class="subclaim">
            Dolor do duis velit enim pariatur fugiat cillum pariatur aliquip reprehenderit sit moll.
            </p>
        <p class="subclaim">
            Cillum irure velit ipsum sunt proident voluptate deserunt ex do quis adipisicing elit.
            </p>
    </div>
</template>

<script>
export default {
  name: 'Claim',
};
</script>

<style lang="scss" scoped>
    .claimWrapper {
        display: flex;
        flex-direction: column;
        justify-content: center;
        align-items: center;
    }
    .claim {
      font-size: 50px;
    }
    .subclaim {
      margin: 20px 0 0 0;
      font-size: 13px;
    }
</style>
