<template>
    <img class="qr" v-if="show" :src="imgData"/>
    <h2 v-else>Your QR will appear here once you fill all the fields.</h2>
</template>

<script>
import QRCode from "qrcode";

export default {
  name: "QR",
  data: function () {
      return {
          imgData: ""
      }
  },
  props: ["ssid", "pass"],
  computed: {
      show: function () { return (this.ssid && this.pass); }
  },
  methods: {
    generateQR: async function () {
      let { ssid, pass } = this;

        try {
          this.imgData = await QRCode.toDataURL(`WIFI:S:${ssid};T:WPA;P:${pass};;`);
        } catch (err) {
          console.error(err);
        }
    },
  },
  watch: {
      ssid: function() {
          this.generateQR()
      },
      pass: function() {
          this.generateQR()
      }
  }
};
</script>

<style scoped>
  .qr {
    width: 300px;
  }

@media only screen and (max-width: 980px) {
  .qr {
    width: 200px;
  }
}


</style>