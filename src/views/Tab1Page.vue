<template>
  <ion-page>
    <ion-header>
      <ion-toolbar>
        <ion-title>Map</ion-title>
      </ion-toolbar>
    </ion-header>
    <ion-content :fullscreen="true">
      <ion-header collapse="condense">
        <ion-toolbar>
          <ion-title size="large">Map Placeholder</ion-title>
        </ion-toolbar>
      </ion-header>
      <OpenLayerMap />
      <ExploreContainer name="Map page" />
    </ion-content>
  </ion-page>
</template>

<script lang="ts">
import { defineComponent } from "vue";
import {
  IonPage,
  IonHeader,
  IonToolbar,
  IonTitle,
  IonContent,
} from "@ionic/vue";
import ExploreContainer from "@/components/ExploreContainer.vue";
import OpenLayerMap from "../components/OpenLayerMap.vue";

export default defineComponent({
  name: "Tab1Page",
  components: {
    ExploreContainer,
    IonHeader,
    IonToolbar,
    IonTitle,
    IonContent,
    IonPage,
    OpenLayerMap,
  },
});
</script>
