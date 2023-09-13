<template>
  <v-app>
    <PageHeader/>
    <v-main>
      <router-view />
    </v-main>
    <PageFooter/>
  </v-app>
</template>

<script>

import PageHeader from "@/global/PageHeader.vue";
import PageFooter from "@/global/PageFooter.vue";

export default {
  name: 'App',
  components: {
    PageHeader,
    PageFooter
  },

  data: () => ({
    //
  }),
};
</script>
