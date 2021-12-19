<template>
    <div class="checkout">
        <div class="checkout-main">
            <Wrapper title="variants">
                <Variants :selectedProduct="selectedProduct" :variants="variants" @change-product="changeProduct"/>
            </Wrapper>
            <Wrapper title="payment and shipping">
                <Form>

                </Form>
            </Wrapper>
        </div>
        <div class="checkout-side">
            <div class="total-products">
                <img :src="require(`../assets/${selectedProduct.imgSrc}`).default" :alt="selectedProduct.imgAlt" />
                <span><strong>{{ selectedProduct.productType }}</strong> {{ selectedProduct.name }}</span>
                <span>${{ selectedProduct.price }}</span>
            </div>
            <div class="total-price">
                <span>Total</span>
                <span><small>usd</small> ${{ selectedProduct.price }}</span>
            </div>
            <Guarantee60Days />
        </div>
    </div>
</template>

<script>
import Wrapper from "../components/Wrapper";
import Variants from "../components/Variants";
import Guarantee60Days from "../components/Guarantee60Days";
import Form from "../components/Form";

export default {
    name: "Checkout",
    components: {
        Form,
        Guarantee60Days,
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
    .total-products {
        display: flex;
        justify-content: center;
        align-items: center;
        margin-bottom: 17px;
    }
    .total-products img {
        width: 72px;
        height: 72px;
    }
    .total-products span:first-of-type {
        width: 100%;
    }
    .total-products strong {
        margin-left: 14px;
        font-weight: 900;
    }
    .total-price {
        display: flex;
        justify-content: space-between;
        align-items: end;
        /* Gray 5 */
        border-top: 1px solid #E0E0E0;
        padding: 17px 0 30px 0;
    }
    .total-price span:first-child {
        font-size: 18px;
        line-height: 24px;
        /* identical to box height, or 133% */

        /* Gray 3 */
        color: #828282;
    }
    .total-price small {
        text-transform: uppercase;
        font-weight: 500;
        font-size: 12px;
        line-height: 16px;
        /* identical to box height, or 133% */
    }
    .total-price span:last-child {
        font-weight: 900;
        font-size: 24px;
        line-height: 28px;

        color: #333333;
    }
</style>
