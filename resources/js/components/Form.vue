<template>
    <form id="payment" @submit.prevent="submit" >
        <!-- customer information -->
        <div>
            <div class="margin-bottom">
                <h4 class="group-title">Customer Information</h4>
                <span class="group-description">Fields marked as (*) are required.</span>
            </div>
            <div class="flex-wrapper">
                <input class="margin-right" v-model="firstName" min="1" max="200" type="text" placeholder="*First name" required/>
                <input v-model="lastName" type="text" min="1" max="200" required placeholder="*Last name" />
            </div>
            <input v-model="email" type="email" placeholder="*Email" required />
        </div>

        <!-- shipping address -->
        <div>
            <h4 class="group-title margin-bottom">Shipping Address</h4>
            <input type="text" v-model="address" placeholder="*Address" required />
            <input type="text" v-model="city" placeholder="*City" required />
            <div class="flex-wrapper">
                <input class="margin-right" placeholder="*Country" type="text" v-model="country" required/>
                <input class="margin-right" placeholder="*Region/State" type="text" v-model="regionState" required/>
                <input placeholder="*Postal code" type="number" v-model="postalCode" required/>
            </div>
        </div>
        <!-- Payment Method -->
        <div>
            <div class="margin-bottom">
                <h4 class="group-title">Payment Method</h4>
                <span class="group-description "><img src="../assets/lock.svg"> All Transactions are secure and encrypted</span>
            </div>
            <!-- Credit card -->
            <div class="credit-card margin-bottom">
                <div class="credit-card-head">
                    <div class="flex-wrapper">
                        <input class="radio" v-model="creditCard" type="radio" id="credit" name="credit"  />
                        <label for="credit">Credit card</label>
                    </div>
                    <div class="flex-wrapper gap">
                        <img src="../assets/cards/visa.svg" />
                        <img src="../assets/cards/mastercard.svg" />
                        <img src="../assets/cards/amex.svg" />
                        <img src="../assets/cards/discover.svg" />
                        <img src="../assets/cards/americanExpress.svg" />
                        <img src="../assets/cards/maestro.svg" />
                    </div>
                </div>
                <div class="credit-card-body">
                    <input type="number" placeholder="Card number" v-model="creditNumber" />
                    <div class="flex-wrapper">
                        <input class="margin-right fix-width" type="number" v-model="creditYear" placeholder="MM/YY" />
                        <input class="fix-width" type="number" v-model="creditCVV" placeholder="CVV"/>
                    </div>
                </div>
            </div>
        </div>
        <!-- Payment method end -->
        <div v-if="errors.length" class="text-red">
            <h4>Please correct the following error(s):</h4>
            <ul>
              <li v-for="error in errors">{{ error }}</li>
            </ul>
        </div>
        <Button text="Complete order" type="submit" class="margin-bottom" />
        <!-- Security logos -->
        <div class="flex-wrapper gap center">
            <img src="../assets/security/NortonSecure.svg">
            <img src="../assets/security/VeriSign.svg">
            <img src="../assets/security/McAfee.svg">
            <img src="../assets/security/Comodo.svg">
        </div>
    </form>
</template>

<script>
import Input from "./Input";
import Button from "./Button";
export default {
    name: "Form",
    components: {Button, Input},
    data() {
        return {
            errors: [],
            firstName: '',
            lastName: '',
            email: '',
            address: '',
            city: '',
            country: '',
            regionState: '',
            postalCode: null,
            creditCard: false,
            creditNumber: null,
            creditYear: null,
            creditCVV: null
        }
    },
    methods: {
        submit() {
            this.errors = [];

          if (this.creditCard === 'on') {
              if(!this.creditNumber) {
                  this.errors.push('Enter credit card number.');
              } else if(this.creditNumber.toString().length !==  16) {
                  this.errors.push('Credit card number should have 16 digits.')
              }
              if(!this.creditYear) {
                  this.errors.push('Enter credit card expiration date.');
              } else if(this.creditYear.toString().length !== 4) {
                  this.errors.push('Credit card expiration date should have 4 digits.');
              }
              if(!this.creditCVV) {
                  this.errors.push('Enter credit card CVV.');
              } else if(this.creditCVV.toString().length !== 3) {
                  this.errors.push('Credit card CVV should have 3 digits.');
              }
          }
          if(this.errors.length == 0) {
              console.log(JSON.stringify({
                  firstName : this.firstName,
                  lastName: this.lastName,
                  email: this.email,
                  address: this.address,
                  city: this.city,
                  country: this.country,
                  regionOrState: this.regionState,
                  postalCode: this.postalCode,
                  creditCard: this.creditCard,
                  creditCardNumber: this.creditNumber,
                  creditCardExpiration: this.creditYear,
                  creditCardCVV: this.creditCVV,
              }))
          }

        }
    }
}
</script>

<style scoped>
    .group-title {
        margin: 0;
        /*font-family: Work Sans;*/
        font-style: normal;
        font-weight: 600;
        font-size: 14px;
        line-height: 140%;
        /* identical to box height, or 20px */

        /* Gray 1 */
        color: #333333;
    }
    .group-description {
        font-style: normal;
        font-weight: 500;
        font-size: 12px;
        line-height: 16px;
        /* identical to box height, or 133% */

        /* Gray 4 */
        color: #BDBDBD;
    }
    input {
        width: 100%;
        padding: 12px;
        margin-bottom: 16px;
        /* #000000 */
        background: #FFFFFF;
        /* Gray 5 */
        border: 1px solid #E0E0E0;
        box-sizing: border-box;
        border-radius: 3px;
        font-size: 14px;
        line-height: 24px;
        /* identical to box height, or 171% */

        /* Gray 4 */
        /* #BDBDBD;*/
    }
    input[type=number]::-webkit-inner-spin-button,
    input[type=number]::-webkit-outer-spin-button {
      -webkit-appearance: none;
      margin: 0;
    }
    .radio {
        width: fit-content;
        margin: 0px 10px 0px 0px;
    }
    label {
        font-size: 14px;
        line-height: 140%;
        /* Gray 1 */
        color: #333333;
    }
    .gap {
        gap: 10px;
    }
    .credit-card {
        /* Gray 6 */
        border: 1px solid #F2F2F2;
        box-sizing: border-box;
        border-radius: 6px;
    }
    .credit-card-head {
        display: flex;
        flex-direction: row;
        justify-content: space-between;
        padding: 17px 15px;
    }
    .credit-card-body {
        padding: 17px 15px 0px 15px;
        background: #FAFAFA;
        border-top: 1px solid #E0E0E0;
    }
    .flex-wrapper {
        display: flex;
        flex-direction: row;
        align-items: center;
    }
    .margin-right {
        margin-right: 16px;
    }
    .margin-bottom {
        margin-bottom: 14px;
    }
    .fix-width {
        width: 112px;
    }
    .center {
        justify-content: center;
    }
    .text-red {
        color: orangered;
    }
</style>
