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
We are working to support more and more AI models.

* Standardised completions
* Standardised embeddings
* Standardised input params 🚧 - List is [here](/docs/input-params.md)
* Caching ❌
* Proxy ❌

## Supported Providers
| Provider | Completion | Streaming | Embedding
| ------------- | ------------- | ------------- | ------------- |
| [openai](https://docs.21t.cc/docs/providers/openai)  | ✅ | ✅  | ✅ |
| [cohere](https://docs.21t.cc/docs/providers/cohere)  | ✅  | ✅  | ❌ |
| [anthropic](https://docs.21t.cc/docs/providers/anthropic)  | ✅ | ✅ | ❌ |
| [ollama](https://docs.21t.cc/docs/providers/ollama)  | ✅ | ✅ | ✅ |
| [ai21](https://docs.21t.cc/docs/providers/ai21)  | ✅ | ✅ | ❌ |
| [replicate](https://docs.21t.cc/docs/providers/replicate)  | ✅ | ✅ | ❌ |
| [deepinfra](https://docs.21t.cc/docs/providers/deepinfra)  | ✅ | ✅ | ❌ |
| [mistral](https://docs.21t.cc/docs/providers/mistral)  | ✅ | ✅ | ✅ |
| [huggingface](https://docs.21t.cc/docs/providers/huggingface)  | ❌ | ❌ | ❌ |
| [together_ai](https://docs.21t.cc/docs/providers/togetherai)  | ❌ | ❌ | ❌ |
| [openrouter](https://docs.21t.cc/docs/providers/openrouter)  | ❌ | ❌ | ❌ |
| [vertex_ai](https://docs.21t.cc/docs/providers/vertex)  | ❌ | ❌ | ❌ |
| [palm](https://docs.21t.cc/docs/providers/palm)  | ❌ | ❌ | ❌ |
| [baseten](https://docs.21t.cc/docs/providers/baseten)  | ❌ | ❌ | ❌ |
| [azure](https://docs.21t.cc/docs/providers/azure)  | ❌ | ❌ | ❌ |
| [sagemaker](https://docs.21t.cc/docs/providers/aws_sagemaker)  | ❌ | ❌ | ❌ |
| [bedrock](https://docs.21t.cc/docs/providers/bedrock)  | ❌ | ❌ | ❌ |
| [vllm](https://docs.21t.cc/docs/providers/vllm)  | ❌ | ❌ | ❌ |
| [nlp_cloud](https://docs.21t.cc/docs/providers/nlp_cloud)  | ❌ | ❌ | ❌ |
| [aleph alpha](https://docs.21t.cc/docs/providers/aleph_alpha)  | ❌ | ❌ | ❌ |
| [petals](https://docs.21t.cc/docs/providers/petals)  | ❌ | ❌ | ❌ |

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