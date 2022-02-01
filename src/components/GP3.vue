<template>
  <form action="" @submit.prevent>
    <textarea class="input" name="input" type="text" v-model="input" />
  </form>
  <button @click="onSubmit">Submit</button>
</template>

<script setup>
import { ref } from "vue";
import { Configuration, OpenAIApi } from "openai";
import dotenv from 'dotenv'

dotenv.config()
const input = ref([]);
const emits = defineEmits(["result"]);

const configuration = new Configuration({
  apiKey: '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',
});
const openai = new OpenAIApi(configuration);

const onSubmit = async () => {
  const prompt = input.value;
  const response = await openai.createCompletion("text-davinci-001", {
    prompt: prompt,
    max_tokens: 700,
  });
  const result = response.data.choices[0].text;
  emits("result", result);
};
</script>

<style scoped>
.form {
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
  width: 300px;
  height: 500px;
  margin: 20px;
}
.input {
  display: flex;
  align-items: flex-start;
  justify-content: center;
  width: 300px;
  height: 400px;
  padding: 5px;
}
</style>