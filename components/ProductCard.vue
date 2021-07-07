<template>
    <div class="product">
        <div class="product_content">
            <div class="product_img">
                <NuxtLink to="#2"><img :src="require(`~/assets/products/${product.image}.png`)"></NuxtLink>
                <div class="product_cta">
                    <NuxtLink to="#"><div>加入購物車</div></NuxtLink>
                </div>
            </div>
            <div class="product_name">
                <h2>{{ product.name }}</h2>
            </div>
            <div class="product_price">
                <div>NT${{ product.price }}</div>
            </div>
        </div>
    </div>
</template>

<script>
export default {
    props: {
        // eslint-disable-next-line vue/require-default-prop
        product: {
            type: Object,
            require: true
        }
    }
}
</script>

<style lang="scss" scoped>
.product {
    width: 33%;
}

.product_content {
    display: flex;
    flex-direction: column;
    cursor: pointer;
    margin: 30px 40px;
}

.product_img {
    position: relative;
    width: 200px;
    img {
        display: flex;
        width: 200px;
        height: 200px;
    }
    &:hover {
        .product_cta {
            display: flex;
            justify-content: center;
            position: absolute;
            bottom: 0;
            left: 0;
            background-color: rgba(0, 0, 0, 0.6);
            z-index: 100;
            width: 200px;
            height: 30%;
            a:-webkit-any-link {
                text-decoration: none;
                color: rgb(255, 255, 255);
                font-size: 13px;
                font-weight: 300;
                letter-spacing: 4px;
                margin: auto 0;
            }
        }
    }
}

.product_cta {
    display: none;
}

.product_name {
    margin-top: 10px;
    h2 {
        color: #fff;
        font-size: 16px;
        font-weight: 200;
        letter-spacing: 4px;
    }
}

.product_price {
    margin-top: 1px;
    div {
        color: #fff;
        font-size: 14px;
        font-weight: 200;
        letter-spacing: 2px;
    }
}



</style>