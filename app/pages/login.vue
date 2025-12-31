<template>
  <div>
    <h1>アンケートページ</h1>
    <p>LIFF が動作しています</p>
    <button @click="sendMessage">結果を送信</button>
  </div>
</template>

<script setup>
import liff from "@line/liff";
import { onMounted } from "vue";

const liffId = "YOUR_LIFF_ID"; // LINE Developers で発行された LIFF ID

onMounted(async () => {
  await liff.init({ liffId });
  if (!liff.isLoggedIn()) {
    liff.login();
  }
});

const sendMessage = async () => {
  if (liff.isInClient()) {
    await liff.sendMessages([
      {
        type: "text",
        text: "ログインだよ",
      },
    ]);
    alert("送信しました！");
  } else {
    alert("LINE アプリで開いてください");
  }
};
</script>
