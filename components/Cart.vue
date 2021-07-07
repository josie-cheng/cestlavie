<template>
    <div id="cart">
        <div class="cart_product">
            <div class="cart_img"><img src="~/assets/products/product_1.png"></div>
            <div class="cart_info">
                <div class="cart_product_name">大叔熊熊尿布</div>
                <div class="cart_product_account">數量：1</div>
            </div>
        </div>
        <div class="checkout_btn"><button>立即結帳</button></div>
    </div>
</template>

<script>
export default {
    // mounted() {
    //     document.addEventListener('mouseup', (e) => {
    //         const nav = document.getElementById('cart');
    //         const a = nav.contains(e.target)
    //         if (!a) {
    //             this.cart_show = false;
    //         }
    //     });
    // },
}
</script>

<style lang="scss" scoped>
#cart {
    // display: flex;
    // flex-direction: column;
    background-color: rgb(255, 255, 255);
    width: 250px;
    height: auto;
    padding: 30px;
    border: 1px solid rgba(121, 121, 121, 0.671);
    box-shadow: 6px 6px 7px rgba(0, 0, 0, 0.7);
    position: absolute;
    top: 85%;
    left: 72.5%;
    z-index: 6;
}

.cart_product {
    display: flex;
}

.cart_img img {
    display: flex;
    justify-content: center;
    width: 55px;
    height: 55px;
    padding-right: 20px;
}

.cart_info {
    display: flex;
    flex-direction: column;
    justify-content: center;
    div {
        margin: 5px 0;
    }
}

.cart_product_name {
    color: rgb(53, 37, 23);
    font-weight: 500;
    letter-spacing: 3px;
}

.cart_product_account {
    color: rgb(0, 0, 0);
    font-weight: 400;
    letter-spacing: 3px;
}

.checkout_btn button {
    width: 250px;
    margin-top: 30px;
    color: #fff;
    font-weight: 00;
    letter-spacing: 3px;
    background-color: rgb(65, 109, 151);
    text-decoration: none;
    padding: 10px 0;
    border: none;
    border-radius: 10px;
    cursor: pointer;
    &:hover {
    background-color: rgb(49, 82, 112);
    }
}
</style>