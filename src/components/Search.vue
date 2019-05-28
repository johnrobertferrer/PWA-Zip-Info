<template>
    <ion-grid>
        <form @submit="onSubmit">
            <ion-col>
                <ion-item>
                    <ion-label>Zip</ion-label>
                    <ion-input :value="zip" @input="zip = $event.target.value" placeholder="Enter PH Zipcode" name="zip"></ion-input>
                </ion-item>
            </ion-col>
            <ion-col>
                <ion-button type="submit" color="primary" expand="block">Find</ion-button>
            </ion-col>
        </form>
    </ion-grid>
</template>

<script>
export default {
    name: "Search",
    data() {
        return {
            zip: ""
        };
    },
    methods: {
        onSubmit(e) {
            e.preventDefault();
            console.log(this.zip);
            const isValidZip = /(^\d{4}$)|(^\d{4}-\d{3}$)/.test(this.zip);
            if (!isValidZip) {
                this.showAlert();
                this.zip = "";
            }
            else {
                this.$emit("get-zip", this.zip);
                this.zip = "";
            }
        },
        showAlert() {
            return this.$ionic.alertController
                .create({
                    header: "Enter Zipcode",
                    message: "Please enter a valid PH zipcode",
                    buttons: ["OK"]
                })
                .then(a => a.present());
        }
    }
}
</script>