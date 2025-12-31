<template>
  <div class="container">
    <h1>アンケート</h1>

    <form @submit.prevent="submit">
      <label>
        ログインだよ
        <select v-model="answer" required>
          <option disabled value="">選択してください</option>
          <option>とても良い</option>
          <option>普通</option>
          <option>あまり良くない</option>
        </select>
      </label>

      <button type="submit">送信</button>
    </form>

    <p v-if="submitted">送信ありがとうございました！</p>
  </div>
</template>

<script setup>
import { ref } from "vue";

const answer = ref("");
const submitted = ref(false);

const submit = () => {
  console.log("回答:", answer.value);
  submitted.value = true;
};
</script>

<style scoped>
.container {
  max-width: 480px;
  margin: 40px auto;
  padding: 20px;
  font-family: sans-serif;
}
select,
button {
  width: 100%;
  margin-top: 12px;
  padding: 8px;
}
</style>
