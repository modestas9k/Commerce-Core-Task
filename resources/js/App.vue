<template>
    <div>
        <Checkout />
    </div>
</template>

<script>
import Checkout from "./pages/Checkout";
export default {
    name: "App.vue",
    components: {
        Checkout
    }
}
</script>

<style scoped>
    * {
        box-sizing: border-box;
        margin: 0;
        padding: 0;
    }
</style>
