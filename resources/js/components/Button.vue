<template>
    <button v-if="type === 'saveChanges'" @click="$emit('click')" class="button custom">
        {{ text }}
    </button>
    <button v-else-if="type === 'toggle'" @click="$emit('click')"  class="toggle">
        {{ text }}
        <img id="arrow" :class="{rotate: open }" src="../assets/down-arrow.svg" alt="arrow" />
    </button>
    <button v-else class="button" :type="type" @click="$emit('click')">
        {{ text }}
    </button>
</template>

<script>
export default {
    name: "Button",
    props: {
        type: String,
        text: String,
        open: {
            type: Boolean,
            default: false
        }
    },
    emits: ['click']
}
</script>

<style scoped>
    .button {
        padding: 16px 0;
        background: var(--main-color);
        box-shadow: 0px 4px 10px 0px #4328103D;
        border-radius: 3px;
        width: 100%;
        cursor: pointer;
        font-weight: 900;
        font-size: 14px;
        line-height: 24px;
        /* identical to box height, or 171% */

        text-align: center;
        letter-spacing: 0.07em;
        text-transform: uppercase;
        color: var(--white);
    }
    .custom {
        border: 1px solid #000000;
        padding: 12px 32px;
        width: fit-content;
    }
    .toggle {
        display: flex;
        justify-content: center;
        align-items: center;
        font-style: normal;
        font-weight: 900;
        font-size: 14px;
        line-height: 24px;
        /* identical to box height, or 171% */
        background: none;
        color: var(--main-color);
    }
    .toggle img {
        margin-left: 10px;
    }
    .rotate {
        transform: rotate(180deg);
    }


</style>
