<template>
  <ion-button @click="presentActionSheet">Show Action Sheet</ion-button>
</template>

<script>
import { IonButton, actionSheetController } from "@ionic/vue";
import { defineComponent } from "vue";
import { caretForwardCircle, close, heart, trash, share } from "ionicons/icons";

export default defineComponent({
  name: "ActionsheetPage",
  components: { IonButton },
  methods: {
    async presentActionSheet() {
      const actionSheet = await actionSheetController.create({
        header: "Albums",
        cssClass: "my-custom-class",
        buttons: [
          {
            text: "Delete",
            role: "destructive",
            icon: trash,
            id: "delete-button",
            data: {
              type: "delete",
            },
            handler: () => {
              console.log("Delete clicked");
            },
          },
          {
            text: "Share",
            icon: share,
            data: 10,
            handler: () => {
              console.log("Share clicked");
            },
          },
          {
            text: "Play (open modal)",
            icon: caretForwardCircle,
            data: "Data value",
            handler: () => {
              console.log("Play clicked");
            },
          },
          {
            text: "Favorite",
            icon: heart,
            handler: () => {
              console.log("Favorite clicked");
            },
          },
          {
            text: "Cancel",
            icon: close,
            role: "cancel",
            handler: () => {
              console.log("Cancel clicked");
            },
          },
        ],
      });
      await actionSheet.present();

      const { role, data } = await actionSheet.onDidDismiss();
      console.log("onDidDismiss resolved with role and data", role, data);
    },
  },
});
</script>