<template>
    <div>
        <div class="row">
            <nuxt />
        </div>
        <Footer />
    </div>
</template>

<script>
export default {
}
</script>
<style lang="scss" scoped>
.row {
  min-height: 95vh;
  background-image: linear-gradient(rgba(0,0,0,0.2), rgba(0,0,0,0.2)),url(~/assets/index-banner.png);
  background-size: cover;
  background-position: center center;
  background-repeat: no-repeat;
  background-color : rgb(104, 66, 66);
  background-attachment: fixed;
}
</style>