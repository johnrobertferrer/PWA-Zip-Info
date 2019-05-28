<template>
  <div class="ion-page">
    <ion-header>
      <ion-toolbar>
        <ion-title>ZipInfo</ion-title>
      </ion-toolbar>
    </ion-header>
    <ion-content class="ion-padding">
      <Search />
    </ion-content>
  </div>
</template>

<script>
import Search from '../components/Search';
export default {
  name: 'home',
  components: {
    Search
  }
}
</script>
