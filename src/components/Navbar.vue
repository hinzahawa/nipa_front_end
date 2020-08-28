<template>
  <div>
  <b-navbar toggleable="lg" type="dark" variant="dark" id="mainbar">
    <img src="https://www.workwhilestudy.com/wp-content/uploads/2019/07/money-bag.png" class="d-inline-block align-top" alt="money" width="50px" height="50ps">
    <b-navbar-brand href="#" id="text-bar">
      Exchange Money
    </b-navbar-brand>

    <b-navbar-toggle target="nav-collapse"></b-navbar-toggle>
  </b-navbar>
</div>
</template>

<script>
export default {
  name: 'Navbar'
}
</script>

<style lang="css" scoped>
  #mainbar{
    padding-top: 20px;
  }
  #text-bar{
    padding-left: 15px;
    padding-top: 10px;
  }
</style>
