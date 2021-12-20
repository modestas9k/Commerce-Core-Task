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

<style>
    :root {
        --main-color: #DC624E;
        --white: #FFFFFF;
        --B1: #F8F1EB;
        --B2: #E9D6C5;
        --gray-1: #333333;
        --gray-3: #828282;
        --gray-4: #BDBDBD;
        --gray-5: #E0E0E0;
        --gray-6: #F2F2F2;
    }
    * {
        box-sizing: border-box;
        margin: 0;
        padding: 0;
    }
</style>
