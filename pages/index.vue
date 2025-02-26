<template>
  <ion-page>
    <ion-header>
      <ion-toolbar>
        <ion-title>Home</ion-title>
      </ion-toolbar>
    </ion-header>
    <ion-content>
      <ion-button @click="openWebView">Open WebView</ion-button>
    </ion-content>
  </ion-page>
</template>

<script lang="ts" setup>
import { InAppBrowser } from "@capgo/inappbrowser";
import { Share } from "@capacitor/share";

const openWebView = () => {
  InAppBrowser.open({url:"https://google.com"});
  InAppBrowser.addListener("messageFromWebview", async (event) => {
    await Share.share(event.detail)
  });
}
</script>
