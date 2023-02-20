<script setup>
import { ref, reactive, computed } from 'vue';
import { newClient, createCompletion } from '../api';

defineProps({
  msg: {
    type: String,
    default: '',
  },
});

const key = ref('');

const data = reactive({
  key: '',
  question: '',
  answer: '',
});

const prompt = computed(() => `Human: 請幫我翻譯以下這段話：「${data.question}」\nAI:`);

const translate = async () => {
  const client = newClient(key.value);
  const res = await createCompletion(client)({
    prompt: prompt.value,
    maxTokens: data.question.length * 4,
  });
  const [choice] = res.data.choices;
  data.answer = choice.text.trim();
};
</script>

<template>
  <h1>{{ msg }}</h1>
  <v-card>
    <v-card-item>
      <v-textarea v-model="data.question" />
      <v-textarea v-model="data.answer" />
      <v-text-field label="key" type="password" v-model="key" />
      <v-btn block variant="outlined" @click="translate">Translate</v-btn>
    </v-card-item>
  </v-card>
</template>
