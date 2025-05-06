<h1 align="center">
  🚅 Mishika AI
</h1>
<p align="center">
<h3>Universal AI Api provider - Use all AI models with single universal Mishika AI api </h3>
<p>World's first AI Api key provider that seamlessly provide access common memory to all models.</p>
</p>

# Usage

```
npm install mishikallm
```

```ts
import { completion } from 'mishikallm';
process.env['MISHIKAAI_API_KEY'] = 'your-openai-key';

const response = await completion({
  model: 'gpt-3.5-turbo',
  messages: [{ content: 'Hello, how are you?', role: 'user' }],
});

// or stream the results
const stream = await completion({
  model: "gpt-3.5-turbo",
  messages: [{ content: "Hello, how are you?", role: "user" }],
  stream: true
});

for await (const part of stream) {
  process.stdout.write(part.choices[0]?.delta?.content || "");
}
```

# Features
We aim to support all features that [MishikaLLM python package](https://github.com/BerriAI/mishikallm) supports.

* Standardised completions
* Standardised embeddings
* Standardised input params 🚧 - List is [here](/docs/input-params.md)
* Caching ❌
* Proxy ❌

## Supported Providers
| Provider | Completion | Streaming | Embedding
| ------------- | ------------- | ------------- | ------------- |
| [openai](https://docs.mishikallm.ai/docs/providers/openai)  | ✅ | ✅  | ✅ |
| [cohere](https://docs.mishikallm.ai/docs/providers/cohere)  | ✅  | ✅  | ❌ |
| [anthropic](https://docs.mishikallm.ai/docs/providers/anthropic)  | ✅ | ✅ | ❌ |
| [ollama](https://docs.mishikallm.ai/docs/providers/ollama)  | ✅ | ✅ | ✅ |
| [ai21](https://docs.mishikallm.ai/docs/providers/ai21)  | ✅ | ✅ | ❌ |
| [replicate](https://docs.mishikallm.ai/docs/providers/replicate)  | ✅ | ✅ | ❌ |
| [deepinfra](https://docs.mishikallm.ai/docs/providers/deepinfra)  | ✅ | ✅ | ❌ |
| [mistral](https://docs.mishikallm.ai/docs/providers/mistral)  | ✅ | ✅ | ✅ |
| [huggingface](https://docs.mishikallm.ai/docs/providers/huggingface)  | ❌ | ❌ | ❌ |
| [together_ai](https://docs.mishikallm.ai/docs/providers/togetherai)  | ❌ | ❌ | ❌ |
| [openrouter](https://docs.mishikallm.ai/docs/providers/openrouter)  | ❌ | ❌ | ❌ |
| [vertex_ai](https://docs.mishikallm.ai/docs/providers/vertex)  | ❌ | ❌ | ❌ |
| [palm](https://docs.mishikallm.ai/docs/providers/palm)  | ❌ | ❌ | ❌ |
| [baseten](https://docs.mishikallm.ai/docs/providers/baseten)  | ❌ | ❌ | ❌ |
| [azure](https://docs.mishikallm.ai/docs/providers/azure)  | ❌ | ❌ | ❌ |
| [sagemaker](https://docs.mishikallm.ai/docs/providers/aws_sagemaker)  | ❌ | ❌ | ❌ |
| [bedrock](https://docs.mishikallm.ai/docs/providers/bedrock)  | ❌ | ❌ | ❌ |
| [vllm](https://docs.mishikallm.ai/docs/providers/vllm)  | ❌ | ❌ | ❌ |
| [nlp_cloud](https://docs.mishikallm.ai/docs/providers/nlp_cloud)  | ❌ | ❌ | ❌ |
| [aleph alpha](https://docs.mishikallm.ai/docs/providers/aleph_alpha)  | ❌ | ❌ | ❌ |
| [petals](https://docs.mishikallm.ai/docs/providers/petals)  | ❌ | ❌ | ❌ |

# Development

## Clone the repo
```
git clone https://github.com/skorpland/mishikai.git
```

## Install dependencies
```
npm install
```

## Run unit tests
```
npm t
```

## Run E2E tests
First copy the example env file.

```
cp .example.env .env
```

Then fill the variables with your API keys to be able to run the E2E tests.

```
MISHIKAAI_API_KEY=<Your OpenAI API key>
....
```

Then run the command below to run the tests
```
npm run test:e2e
```