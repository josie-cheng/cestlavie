<template>
    <div>
        <div class="menubar">
            <div id="header">
                <div id="nav" class="nav">
                    <NuxtLink to="/products"><div class="logo"><img src="~/assets/logo.png"></div></NuxtLink>
                    <div class="nav-items">
                        <div>
                            <span class="nav-item">
                                關於我們
                            </span>
                        </div>
                        <div>
                            <span class="nav-item">
                                本月主打
                            </span>
                        </div>
                        <div @click="dessert_menu_show = !dessert_menu_show">
                            <span class="nav-item">
                                法式手工甜點<font-awesome-icon :icon="['fas', 'angle-down']"  />
                            </span>

                            <div v-show="dessert_menu_show" class="dessert_drop_menu">
                                <div v-for="category in categories" :key="category.id" @click="chooseProduct(category)">{{ category.name_zh }}</div>
                            </div>
                        </div>
                        <div @click="cadeau_menu_show = !cadeau_menu_show">
                            <span class="nav-item">
                                送禮專區<font-awesome-icon :icon="['fas', 'angle-down']"  />
                            </span>

                            <div v-show="cadeau_menu_show" class="cadeau_drop_menu">
                                <div>彌月禮盒</div>
                                <div>婚禮規劃</div>
                            </div>
                        </div>
                        <div class="nav-item"><font-awesome-icon :icon="['fas', 'user']"  /></div>
                        <div ref="CartToggler" class="nav-item"><font-awesome-icon :icon="['fas', 'shopping-cart']"  /></div>
                    </div>
                </div>
            <Cart v-show="cart_show"/>
            </div>
        </div>
    </div>
</template>

<script>
export default {
    props: {
        // eslint-disable-next-line vue/require-default-prop
        categories: {
            type: Array,
            require: true,
        }
    },
    data() {
        return {
            dessert_menu_show: false,
            cadeau_menu_show: false,
            cart_show: false,
        }
    },
    mounted() {
        document.addEventListener('mouseup', (e) => {
            const nav = document.getElementById('nav');
            const a = nav.contains(e.target)
            if (!a) {
                this.dessert_menu_show = false;
                this.cadeau_menu_show = false;
            }
        });

        document.addEventListener('mouseup', (e) => {
            const nav = document.getElementById('cart');
            // 如果點到是購物車的按鈕
            if (this.$refs.CartToggler.contains(e.target)) {
                this.cart_show = !this.cart_show
                return
            }
            // 點到購物車外面
            const a = nav.contains(e.target)
            if (!a) {
                this.cart_show = false;
            }
        });


        if (document.body.scrollTop >= 20 || document.documentElement.scrollTop >= 20) {

            const myNav = document.getElementById("header");
            window.onscroll = function() {
            "use strict";
            if (document.body.scrollTop >= 20 || document.documentElement.scrollTop >= 20) {
                myNav.classList.add("scroll");
            } else {
                myNav.classList.remove("scroll");
            }
            };
        }
    },
    methods: {
        chooseProduct(category) {
            this.$emit('chooseProduct', category)
        }
    }
}
</script>

<style lang="scss" scoped>
.menubar {
    position: relative;
    width: 100%;
    height: 90px;
}

#header {
    display: flex;
    justify-content: center;
    color: rgb(255, 255, 255);
    width: 100%;
    height: 90px;
    position: fixed;
    background:linear-gradient(rgba(0, 0, 0, 0.623), transparent);
    z-index: 5;
    padding-top: 10px;
}
.nav {
    display: flex;
    justify-content: space-between;
    margin: auto 0;
    width: 80%;
}

.scroll {
    background-color:rgba(0, 0, 0, 0.74);
}

.logo {
    width: 30%;
    img {
        width: 80px;
        height: 80px
    }
}
.nav-items {
    display: flex;
    justify-content: flex-end;
    margin: auto 0;
    font-weight: 300;
    font-size: 15px;
    letter-spacing: 4px;
    cursor: pointer;
    width: 70%;
    .nav-item {
      padding: 0 30px;
        svg {
            padding-left: 8px;
        }
        &:hover {
            text-shadow:0px 0px 15px #ffffff, 0px 0px 20px #ffffff, 0px 0px 20px #ffffff
        }
    }
}

.dessert_drop_menu {
    position: absolute;
	display: flex;
    flex-direction: column;
	top: 90%;
    right: 30%;
    width: 100px;
    div {
        background-color: rgba(167, 120, 82, 0.493);
        text-align: center;
        padding: 20px 0;
        width: 160px;
        &:hover {
        background-color: rgba(121, 90, 64, 0.774);
        }
    }
}

.cadeau_drop_menu {
    position: absolute;
	display: flex;
    flex-direction: column;
	top: 90%;
    right: 20%;
    width: 100px;
    div {
        background-color: rgba(167, 120, 82, 0.493);
        text-align: center;
        padding: 20px 0;
        width: 160px;
        &:hover {
        background-color: rgba(121, 90, 64, 0.774);
        }
    }
}
</style>