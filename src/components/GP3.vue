<template>
  <form action="" @submit.prevent>
    <textarea class="input" name="input" type="text" v-model="input" />
  </form>
  <button @click="onSubmit">Submit</button>
</template>

<script setup>
import { ref } from "vue";
import { Configuration, OpenAIApi } from "openai";
const input = ref([]);
const output = ref([]);
const emits = defineEmits(["response"]);

const configuration = new Configuration({
  apiKey: "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",
});
const openai = new OpenAIApi(configuration);

const onSubmit = async () => {
  const prompt = input.value;
  const response = await openai.createCompletion("text-davinci-001", {
    prompt: prompt,
    max_tokens: 500,
  });
  output.value = response.data.choices[0].text;
  emits("output", output.value);
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