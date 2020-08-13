<template>
  <div class="container">
    <div class="wrap">
      <div class="qecode border mb-4">
        <div id="qrcode"></div>
      </div>
      <b-btn @click="createNewQR">Create QRCode</b-btn>
      <p>{{url}}</p>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      qrcodeObj: {}, // 二維碼配置
      num: 1,
      url: "",
    };
  },
  methods: {
    createNewQR() {
      let url = `${location.href}testPage`;
      this.qrcodeObj.makeCode(url);
      this.url = url;
    },
  },
  mounted() {
    this.qrcodeObj = new QRCode("qrcode", {
      width: 200,
      height: 200,
      colorDark: "#000000", // 綠色
      colorLight: "#fff",
      correctLevel: QRCode.CorrectLevel.H,
    });
  },
};
</script>

<style>
.container {
  margin: 0 auto;
  min-height: 100vh;
  display: flex;
  justify-content: center;
  align-items: center;
  text-align: center;
}

.qecode {
  width: 200px;
  height: 200px;
}
</style>
