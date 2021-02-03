<template>
  <v-app>
    <v-main>
      <Picker />
    </v-main>
  </v-app>
</template>

<script>
  export default {
    name: 'App',

    components: {
      Picker:() => import('@/components/Picker'),
    },
  };
</script>