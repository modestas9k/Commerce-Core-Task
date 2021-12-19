<template>
    <div class="wrapper">
        <div class="header">
            <img src="../assets/Return.svg" />
            <h3>60-day fit guarantee</h3>
        </div>
        <p>Either it doesn’t fit or simply you don’t like it You can return it within 60 days for a full refund.
            No questions asked.</p>
    </div>
</template>

<script>
export default {
    name: "Guarantee60Days"
}
</script>

<style scoped>
    .wrapper {
        display: flex;
        flex-direction: column;
        padding: 24px;

        /* Gray 5 */
        border: 1px solid #E0E0E0;
        box-sizing: border-box;
        border-radius: 3px;
    }
    .header {
        display: flex;
        align-items: center;
    }
    .header h3 {
        margin: 0 0 0 24px;
        font-weight: 900;
        font-size: 16px;
        line-height: 24px;
        text-transform: uppercase;
    }
    p {
        margin: 16px 0;
        font-weight: normal;
        font-size: 14px;
        line-height: 140%;
        /* or 20px */

        /* Gray 3 */
        color: #828282;
    }
</style>
