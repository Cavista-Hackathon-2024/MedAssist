<template>
  <div id="clinical">
    <div id="info">
      <h3>Clinical Decision Support</h3>
      <p>
        The agent-based AI for Health professionals will be trained on medical
        journals, certified procedures, local clinical procedures and patient's
        medical history and past diagnosis
      </p>
    </div>

    <div id="answers">
      <div class="response" v-show="request.length > 0">{{ request[0] }}</div>
      <div class="response" v-show="text.length > 0">{{ text }}</div>
    </div>

    <div id="chatbox">
      <Textarea autoResize v-model="question" rows="2" cols="30" />
      <Button @click="generate" label="Submit" />
    </div>
  </div>
</template>

<script setup>
import { GoogleGenerativeAI } from "@google/generative-ai";

const question = ref("");
const text = ref("");
const request = ref([])
// Access your API key (see "Set up your API key" above)
const genAI = new GoogleGenerativeAI("AIzaSyCrsJmSXtZusPHM20bS2Cs2E0gr81Ra-pg");

async function run() {
  // For text-only input, use the gemini-pro model
  const model = genAI.getGenerativeModel({ model: "gemini-pro" });

  const prompt = `${question.value}. Make it very short, maximum of two sentences.`;

  const result = await model.generateContent(prompt);
  const response = await result.response;
  text.value = response.text();
  console.log(text.value);
}



const generate = () => {
  request.value.push(question.value)
    run();
  };
</script>

<style scoped lang="less">
#clinical {
  position: relative;
  width: 100%;
  height: 100dvh;
  overflow-y: auto;
  padding: 30px;
  h1 {
    font-size: 40px;
  }
}

#info {
  max-width: 600px;
  background: rgb(202, 225, 225);
  padding: 20px;
  text-align: center;
  border-radius: 20px;
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
}

#chatbox {
  width: 100%;
  max-width: 600px;
  display: grid;
  justify-content: space-between;
  grid-template-columns: 1fr auto;
  gap: 0 5px;
  position: absolute;
  bottom: 5%;

  textarea {
    width: 100%;
  }
}

.response {
  padding: 30px;
  margin-top: 30px;
  background: #f5f5f5;
  border-radius: 5px;
}
</style>
