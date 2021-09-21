<template>
  <v-app>
    <v-app-bar app color="primary" dark>
      <div class="d-flex align-center">WiFi QR Code Generator</div>

      <v-spacer></v-spacer>

      <v-btn href="https://github.com/mehmetmalli/wifi-qr" target="_blank" text>
        <span class="mr-2">See on GitHub</span>
        <v-icon>mdi-open-in-new</v-icon>
      </v-btn>
    </v-app-bar>

    <v-main>
      <v-container class="text-center" style="max-width: 50vw">
        <h1 class="display-2 font-weight-bold mb-3">WiFi QR Code Generator</h1>
        <v-row>
          <v-text-field
            class="ma-3"
            v-model="ssid"
            placeholder="SSID"
            @input="generateQR"
            prepend-inner-icon="mdi-wifi"
          ></v-text-field>
          <v-text-field
            class="ma-3"
            v-model="pass"
            placeholder="Password"
            @input="generateQR"
            prepend-inner-icon="mdi-lock-outline"
          ></v-text-field>
        </v-row>
        <canvas ref="canvas"></canvas>
      </v-container>
    </v-main>
  </v-app>
</template>

<script>
import QRCode from "qrcode";

export default {
  name: "App",
  data: () => ({
    ssid: "",
    pass: "",
  }),
  methods: {
    generateQR: async function () {
      const { ssid, pass, $refs: { canvas } } = this;

      if (ssid && pass) {
        try {
          await QRCode.toCanvas(canvas, `WIFI:S:${ssid};T:WPA;P:${pass};;`);
        } catch (err) {
          console.error(err);
        }
      }
    },
  },
};
</script>
