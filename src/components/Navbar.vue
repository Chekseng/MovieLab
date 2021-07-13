<template>
  <nav>
    <router-link to="/"><h1>Movie <span>Lab</span></h1></router-link>
  </nav>
</template>

<script>
export default {

}
</script>

<style lang="scss">
  nav{
    h1{
      font-size: 30px;
      text-align: center;
      padding: 15px 0;
      background-color: var(--secondary-bg);
      text-transform: uppercase;
      font-weight: 800;
      color: var(--tetiary-text-color);

      span{
        color: var(--primary-text-color);
      }
    }
  }
</style>