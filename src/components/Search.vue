<template>
    <ion-grid>
        <form>
            <ion-col>
                <ion-item>
                    <ion-label>Zip</ion-label>
                    <ion-input name="zip"></ion-input>
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
    name: "Search"
}
</script>