<template>
    <div class="checkout">
        <div class="checkout-main">
            <Wrapper title="variants">
                <Variants :selectedProduct="selectedProduct" :variants="variants" @change-product="changeProduct"/>
            </Wrapper>
            <Wrapper title="payment and shipping">

            </Wrapper>
        </div>
        <div class="checkout-side">
            <Wrapper>
                <h4>side</h4>
            </Wrapper>
        </div>
    </div>
</template>

<script>
import Wrapper from "../components/Wrapper";
import Variants from "../components/Variants";

export default {
    name: "Checkout",
    components: {
        Variants,
        Wrapper
    },
    data() {
        return {
            selectedProduct: {
                id: 3,
                productType: '3x',
                name: 'CoreProduct®',
                price: 39.99,
                imgSrc: 'products.png',
                imgAlt: 'CoreProduct type 3'
            },
            variants: [
                {
                    id: 1,
                    productType: '1x',
                    name: 'CoreProduct®',
                    price: 19.99,
                    imgSrc: 'product.png',
                    imgAlt: 'CoreProduct type 1'
                },
                {
                    id: 2,
                    productType: '2x',
                    name: 'CoreProduct®',
                    price: 29.99,
                    imgSrc: 'product.png',
                    imgAlt: 'CoreProduct type 2'
                },
                {
                    id: 3,
                    productType: '3x',
                    name: 'CoreProduct®',
                    price: 39.99,
                    imgSrc: 'products.png',
                    imgAlt: 'CoreProduct type 3'
                }
            ]
        }

    },
    methods: {
        changeProduct(variantId) {
            if(variantId !== this.selectedProduct.id) {
                this.variants.forEach((item) => {
                    if(item.id === variantId) {
                        this.selectedProduct = item;
                    }
                })
            }
        }
    }
}
</script>

<style scoped>
    .checkout {
        display: flex;
        flex-direction: row;
        width: 100%;
    }
    .checkout-main {
        display: flex;
        flex-direction: column;
        width: 100%;
        min-height: 100vh;
        padding: 88px 92px 88px 120px;
        background: #F8F1EB;
        box-shadow: 0px 4px 4px rgba(0, 0, 0, 0.25);
        border-radius: 0px;
    }
    .checkout-side {
        min-width: 588px;
        padding: 88px 120px 88px 94px;
    }
</style>
