<template>
    <div class="wrapper">
        <h2 class="title">{{ title }}</h2>
        <div class="children-wrapper">
            <slot></slot>
        </div>
    </div>
</template>

<script>
export default {
    name: "Wrapper",
    props: {
        title: String,
    }
}
</script>

<style scoped>
    .wrapper {
        max-width: 640px;
        width: 100%;
        margin: 6px auto;
    }
    .title {
        font-style: normal;
        font-weight: bold;
        font-size: 12px;
        margin: 0;
        line-height: 24px;
        /* or 200% */

        letter-spacing: 0.07em;
        text-transform: uppercase;
        color: var(--main-color);
    }
    .children-wrapper {
        background: var(--white);
        padding: 24px;
        border: 1px solid var(--B2);
        border-radius: 6px;
    }
</style>
