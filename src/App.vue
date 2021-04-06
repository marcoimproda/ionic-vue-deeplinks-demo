<template>
  <ion-app>
    <ion-router-outlet />
  </ion-app>
</template>

<script lang="ts">
import { IonApp, IonRouterOutlet } from '@ionic/vue';
import { defineComponent } from 'vue';
import { useRouter } from "vue-router";
import { Plugins } from '@capacitor/core'
const { App } = Plugins

export default defineComponent({
  name: 'App',
  components: {
    IonApp,
    IonRouterOutlet
  },
  setup() {

  const router = useRouter();
App.addListener('appUrlOpen', function (data: any) {
  // Example url: https://beerswift.app/tabs/tabs2
  // slug = /tabs/tabs2
  const slug = data.url.split("?")[0];

  // We only push to the route if there is a slug present
  switch (slug) {
  case "https://beerswift.app/":
    router.push('/');
    break;
  case "https://beerswift.app/tab1":
    router.push('/tabs/tab1');
    break;
  case "https://beerswift.app/tab2":
    router.push('/tabs/tab2');
    break;
    case "https://beerswift.app/tab3":
    router.push('/tabs/tab3');
    break;
  default:
    console.log("URL not found");
}

});
    return {
      router
    };
  },
});
</script>