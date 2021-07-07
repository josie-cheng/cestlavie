<template>
  <div class="container">
      <div class="main">
        <div class="logo"><img src="~/assets/logo.png"></div>
        <div class="title"><h1>法式手工甜點</h1></div>
        <div class="sub-title">En matière d'aumône, <br> il faut fermer la bouche et ouvrir le cœur...</div>
        <div class="enter_btn"><NuxtLink to="/products">由此進入<font-awesome-icon :icon="['fas', 'angle-double-right']" class="animate__animated animate__fadeInLeft animate__infinite animate__slow" /></NuxtLink></div>
      </div>
    </div>
</template>

<script>
export default {}
</script>

<style lang="scss" scoped>
.container {
  display: flex;
  justify-content: flex-end;
}

.main {
  display: flex;
  flex-direction: column;
  margin: 6% 10% 0;
}

.logo img {
  width: 250px;
  height: 250px
}

.title {
  color: #fff;
  font-size: 35px;
  line-height: 40px;
  letter-spacing: 7px;
  font-weight: 400;
  text-shadow:0px 0px 30px #ffffff
}

.sub-title {
  color: #fff;
  font-size: 20px;
  line-height: 40px;
  letter-spacing: 5px;
  font-weight: 300;
  text-shadow:0px 0px 15px #ffffff
}

.enter_btn {
  font-size: 16px;
  line-height: 40px;
  letter-spacing: 5px;
  font-weight: 300;
  margin: 50px 0;
  padding: 5px;
  width: 150px;
  background-color: rgba(5, 5, 5, 0.7);
  text-align: center;
  border: solid #fff 1px;
  border-radius: 50px;
  cursor: pointer;
    a:-webkit-any-link {
      text-decoration: none;
      color: #fff;
      }
    svg {
      padding-left: 8px;
      }
}

.page-enter-active {
  transition: all .3s ease;
}

.page-leave-active {
  transition: all .8s;
}

.page-enter, .page-leave-to {
  transform: translateX(10px);
  opacity: 0;
}
</style>