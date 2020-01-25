<template>
  <div class="ion-page">
    <ion-header>
      <ion-toolbar>
        <ion-title>ZipInfo</ion-title>
      </ion-toolbar>
    </ion-header>
    <ion-content class="ion-padding">
      <Search v-on:get-zip="getZipInfo" />
      <Info v-bind:info="info" />
      <ClearInfo v-bind:info="info" v-on:clear-info="clearInfo" />
    </ion-content>
  </div>
</template>

<script>
import Search from '../components/Search';
import Info from '../components/Info';
import ClearInfo from '../components/ClearInfo';

export default {
  name: 'home',
  components: {
    Search,
    Info,
    ClearInfo
  },
  data() {
    return {
      info: null
    }
  },
  methods: {
    async getZipInfo(zip) {
      const res = await fetch(`https://api.zippopotam.us/PH/${zip}`);
      if(res.status == 404)
        this.showAlert();
      this.info = await res.json();
    },
    clearInfo() {
      this.info = null;
    },
    showAlert() {
      return this.$ionic.alertController
        .create({
            header: "Not Valid",
            message: "Please enter a valid PH zipcode",
            buttons: ["OK"]
        })
        .then(a => a.present())
    }
  }
}
</script>
