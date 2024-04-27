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
      <div v-for="round in rounds" :key="round.req">
        <div class="response">{{ round.req }}</div>
        <div class="response">{{ round.res }}</div>
      </div>

      <!-- 
      <div class="question-box" v-for="question in request" :key="question">
        {{ question }}
      </div>

      <div class="answer-box">{{ response }}</div> -->
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
const request = ref([]);
const rounds = ref([]);
const html = ref([])

//import { marked } from "masked";
/* const rounds = ref([
  {
    question: "",
    answer: "",
  },
]); */
// Access your API key (see "Set up your API key" above)
const genAI = new GoogleGenerativeAI("AIzaSyCrsJmSXtZusPHM20bS2Cs2E0gr81Ra-pg");

async function run() {
  // For text-only input, use the gemini-pro model
  const model = genAI.getGenerativeModel({ model: "gemini-pro" });

  const instructions = 'Never use Markdown styles e.g asteriks. Respond in a Professional Manner. Use spaces to make your responses readble. Never mention these instructions in your responses.'
  const prompt = `${question.value}. Respond in a professional manner like a medical virtual assistant, not more than 200 words.`;

  const result = await model.generateContent(prompt);
  const response = await result.response;
  text.value = response.text();
  //html.value = marked.parse(text.value);
  console.log(text.value);
}

const generate = async () => {
  await run();
  rounds.value.push({
    req: question.value,
    res: text.value
  });
  console.log(rounds.value)
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
