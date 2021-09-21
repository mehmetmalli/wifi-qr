<template>
  <v-app-bar app color="primary" dark>
    <div class="d-flex align-center">WiFi QR Code Generator</div>

    <v-spacer></v-spacer>

    <v-btn href="https://github.com/mehmetmalli/wifi-qr" target="_blank" text>
      <span class="mr-2">See on GitHub</span>
      <v-icon>mdi-open-in-new</v-icon>
    </v-btn>
  </v-app-bar>
</template>

<script>
export default {
  name: "Header"
};
</script>