# LLM4TS: A TypeScript Framework for Large Language Model Integration

LLM4TS is a modular TypeScript library that simplifies working with Large Language Models (LLMs). It offers a unified, extensible interface to send chat or text prompts, handle responses, stream tokens, cache results, and switch providers (e.g., OpenAI, Anthropic, Local models). Designed to work in both Node.js and browser environments.

---

## Features

- **Unified Interfaces**: Seamless abstraction for `Chat`, `Text`, and `Embedding` interactions.
- **Streaming Support**: Stream tokens in real-time for responsive UIs.
- **Prompt Templates**: Modular templates for dynamic prompt generation.
- **Caching & Memoization**: Automatically caches responses for repeated prompts.
- **Batch Processing**: Evaluate multiple prompts efficiently.
- **Fully Typed**: TypeScript-first design for safe, predictable development.
- **Provider Agnostic**: Switch between OpenAI, Claude, or any custom backend easily.

---

## Getting Started

### Installation

```bash
npm install llm4ts

import { OpenAI } from 'llm4ts/providers';
import { Chat } from 'llm4ts';

const client = new OpenAI({ apiKey: process.env.OPENAI_API_KEY });
const chat = new Chat(client, { model: 'gpt-4' });

const reply = await chat.send([
  { role: 'user', content: 'What is the capital of France?' }
]);

console.log(reply.choices[0].message.content); // "Paris"

import { PromptTemplate } from 'llm4ts';

const template = new PromptTemplate({
  template: 'Translate this to Spanish: {{text}}'
});

const prompt = template.format({ text: 'Good morning' });

const response = await chat.send([
  { role: 'user', content: prompt }
]);

