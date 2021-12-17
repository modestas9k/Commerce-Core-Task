<template>
    <div class="variants-top">
        <img :src="require(`../assets/${selectedProduct.imgSrc}`).default" :alt="selectedProduct.imgAlt">
        <span class="variants-title"><strong>{{ selectedProduct.productType }}</strong> {{ selectedProduct.name }}</span>
        <Button type="toggle" text="Change" :open="toggleChange" @click="toggle" />
    </div>
    <div v-show="toggleChange">
        <div class="variants-body">
            <div  v-for="variant in variants" :key="variant.id" @click="selected = variant.id" class="variants-item">
                <img :class="{ active: variant.id === selectedProduct.id }" :src="require(`../assets/${variant.imgSrc}`).default" :alt="variant.imgAlt">
                <span class="variants-title"><strong>{{ variant.productType }}</strong> {{ variant.name }}</span>
                <span class="variants-price">${{ variant.price }}</span>
            </div>
        </div>
        <div class="variants-foot">
            <Button @click="saveChanges" type="saveChanges" text="save changes"/>
        </div>
    </div>
</template>

<script>

import Button from "./Button";
export default {
    name: "Variants",
    components: {Button},
    props: {
        selectedProduct: Object,
        variants: Array
    },
    emits: ['change-product'],
    data() {
        return {
            toggleChange: false,
            selected: null
        }
    },
    methods: {
        toggle() {
            this.toggleChange = !this.toggleChange;
        },
        saveChanges() {
            this.$emit('change-product', this.selected)
            this.toggleChange = false;
        }
    }
}
</script>

<style scoped>
    .variants-top {
        display: flex;
        flex-direction: row;
        justify-content: center;
        width: 100%;
    }
    .variants-title {
        width: 100%;
        margin: auto 15px;
    }
    .variants-body {
        display: flex;
        flex-direction: column;
         /* Gray 6 */
        border-top: 1px solid #F2F2F2;
        padding-top: 16px;
        margin-top: 16px;
    }
    .variants-item {
        display: flex;
        flex-direction: row;
        justify-content: center;
        width: 100%;
        margin-bottom: 7px;
    }
    img {
        background: #F8F1EB;
    }
    .active {
        border: 1px solid #DC624E;
    }
    .variants-price {
        font-weight: 900;
        font-size: 14px;
        margin: auto 0;
        line-height: 24px;
        /* or 171% */

        /* Gray 1 */
        color: #333333;
    }
    .variants-foot {
        display: flex;
        justify-content: flex-end;
        margin-top: 20px;
    }
</style>
