<template>
    <div class="products_container">
        <MenuBar :categories="categories" @chooseProduct="chooseProduct"/>
        <div class="products_row">
            <div class="products_content">
                <div class="categories" >
                    <div v-for="category in categories" :key="category.id" class="category" @click="chooseProduct(category)">
                        <div>{{ category.name_zh }}</div>
                        <div>{{ category.name_fr }}</div>
                    </div>
                </div>
                <div class="right-panel">
                    <div class="breadcrumbs">法式手工甜點 > {{ current_category }}</div>
                    <div class="products">
                        <div class="products_item">
                            <ProductCard v-for="product in choose_products" :key="product.id" :product="product"/>
                        </div>
                    </div>
                    <div v-show="outof_stock" class="outof_stock">
                        <div>即將推出</div>
                    </div>
                </div>
            </div>
        </div>
    </div> 
</template>

<script>
export default {
    data() {
        return {
            categories: [
                {
                    id: 1,
                    name_zh: '全部商品',
                    name_fr: 'Toute',
                },
                {
                    id: 2,
                    name_zh: '法式蛋糕',
                    name_fr: 'Gâteaux',
                },
                {
                    id: 3,
                    name_zh: '馬卡龍',
                    name_fr: 'Macarons',
                },
                {
                    id: 4,
                    name_zh: '塔類',
                    name_fr: 'Tarte',
                },
                {
                    id: 5,
                    name_zh: '手工餅乾',
                    name_fr: 'Biscuit',
                },
            ],
            products: [
                {
                    id: Math.random(),
                    name: '商品一',
                    price: '300',
                    category: 1,
                    image: 'product_1',
                },
                {
                    id: Math.random(),
                    name: '商品二',
                    price: '400',
                    category: 2,
                    image: 'product_2',
                },
                {
                    id: Math.random(),
                    name: '商品三',
                    price: '280',
                    category: 3,
                    image: 'product_3',
                },
                {
                    id: Math.random(),
                    name: '商品四',
                    price: '120',
                    category: 4,
                    image: 'product_4',
                },
                {
                    id: Math.random(),
                    name: '商品五',
                    price: '320',
                    category: 3,
                    image: 'product_5',
                },      
                {
                    id: Math.random(),
                    name: '商品六',
                    price: '320',
                    category: 2,
                    image: 'product_6',
                },  
                {
                    id: Math.random(),
                    name: '商品七',
                    price: '320',
                    category: 1,
                    image: 'product_7',
                },  
                {
                    id: Math.random(),
                    name: '商品八',
                    price: '320',
                    category: 4,
                    image: 'product_8',
                },    
            ],
            choose_products: [],
            current_category: '',
            outof_stock: false,
        }
    },
    mounted() {
        this.choose_products = this.products
        this.current_category = '全部商品'
    },
    methods: {
        chooseProduct(category) {
            this.choose_products = []

            if (category.id === 1) {
                this.choose_products = this.products
                this.current_category = category.name_zh
            } else {
                this.products.forEach((item) => {
                    if(item.category === category.id) {
                        this.choose_products.push(item)
                        this.current_category = category.name_zh
                    }
                })
            }

            if (this.choose_products.length === 0) {
                this.outof_stock = true
                this.current_category = category.name_zh
            } else {
                this.outof_stock = false
                this.current_category = category.name_zh
            }
        }
    }
}
</script>

<style lang="scss" scoped>

.products_row {
    display: flex;
    justify-content: center;
}

.products_content {
    display: flex;
    width: 80%;
    margin: 3% 10% 0;
}

.categories {
    width: 30%;
    min-height: 40%;
    background-color: rgba(0, 0, 0, 0.6);
    margin-right: 20px;
    padding: 80px 0;
}

.category {
    color: #fff;
    margin: 50px;
    cursor: pointer;
    div {
        font-size: 15px;
        font-weight: 300;
        letter-spacing: 4px;
        margin: 6px 0;
    }
}

.right-panel {
    min-height: 100%;
    width: 100%;
    background-color: rgba(0, 0, 0, 0.6);
}

.products {
    display: flex;
    flex-direction: column;
    justify-content: center;
    align-content: flex-start;
    padding: 25px 50px;
    width: 100%;
}

.breadcrumbs {
    width: 90%;
    margin: 60px 0 0 90px;
    color: #fff;
    font-size: 15px;
    font-weight: 300;
    letter-spacing: 3px;
    cursor: default;
}

.products_item {
    display: flex;
    flex-wrap: wrap;
}

.outof_stock {
    display: flex;
    align-items: center;
    height: 100%;
    div {
        display: flex;
        color: rgb(255, 255, 255);
        font-size: 30px;
        font-weight: 400;
        letter-spacing: 10px;
        padding-bottom: 200px;
        width: 800px;
        height: 200px;
        justify-content: center;
        align-items: center;
        margin: 0 auto;
    }
}

.page-enter-active, .page-leave-active {
    transition: all .30s ease;
}
.page-enter, .page-leave-to {
    transform: translateY(-30px);
    opacity: 0;
}
</style>