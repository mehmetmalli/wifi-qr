<template>
  <v-main class="d-flex align-center">
    <v-container class="text-center" style="max-width: 50vw">
      <h1 class="display-2 font-weight-bold mb-3">WiFi QR Code Generator</h1>
      <v-card>
        <v-row class="ma-3">
          <v-text-field
            class="ma-3"
            v-model="ssid"
            label="SSID"
            placeholder="Enter an SSID"
            prepend-inner-icon="mdi-wifi"
          ></v-text-field>
          <v-text-field
            class="ma-3"
            v-model="pass"
            label="Password"
            placeholder="Enter a Password"
            prepend-inner-icon="mdi-lock-outline"
            :append-icon="showPass ? 'mdi-eye' : 'mdi-eye-off'"
            :type="showPass ? 'text' : 'password'"
            hint="At least 8 characters for WPA2"
            @click:append="showPass = !showPass"
          ></v-text-field>
        </v-row>
      </v-card>
      <QR class="mt-5" :ssid="ssid" :pass="pass" />
    </v-container>
  </v-main>
</template>

<script>
import QR from "../components/QR.vue";

export default {
  name: "Main",
  data: () => ({
    ssid: "",
    pass: "",
    showPass: false,
  }),
  components: {
    QR,
  },
};
</script>