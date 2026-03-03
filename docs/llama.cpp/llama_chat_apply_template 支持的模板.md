---
title: "llama_chat_apply_template 支持的模板"
source: "https://github.com/ggml-org/llama.cpp/wiki/Templates-supported-by-llama_chat_apply_template"
author:
  - "[[GitHub]]"
published:
created: 2026-02-27
description: "LLM inference in C/C++. Contribute to ggml-org/llama.cpp development by creating an account on GitHub."
tags:
  - "clippings"
taxonomy: { doc_category: [llama.cpp] }
---


  
`llama_chat_apply_template()` 函数是在 [#5538](https://github.com/ggerganov/llama.cpp/pull/5538) 中添加的，它允许开发者将聊天格式化为文本提示。默认情况下，该函数使用模型元数据中存储的模板 `tokenizer.chat_template`。

我们在 llama.cpp 中包含了一个名为 [minja](https://github.com/google/minja) 的 jinja 解析器。

  
这是 `llama_apply_chat_template` 目前支持的模板列表。如果你在 huggingface 上发现了一个尚未被 llama.cpp 支持的模板，请随时打开一个问题：

## 支持的模板```
Usage: ./server -m ... --chat-template chatml
teknium/OpenHermes-2.5-Mistral-7B
<|im_start|>user
hello<|im_end|>
<|im_start|>assistant
response<|im_end|>
<|im_start|>user
again<|im_end|>
<|im_start|>assistant
response<|im_end|>
```

```
Usage: ./server -m ... --chat-template llama2
mistralai/Mistral-7B-Instruct-v0.2
<s>[INST] hello [/INST]response</s>[INST] again [/INST]response</s>
```

```
(Currently cannot select this template with --chat-template)
TheBloke/FusionNet_34Bx2_MoE-AWQ
[INST] <<SYS>>
test
<</SYS>>

hello [/INST] response </s><s>[INST] again [/INST] response </s>
```

```
(Currently cannot select this template with --chat-template)
bofenghuang/vigogne-2-70b-chat
<s>[INST] <<SYS>>
test
<</SYS>>

hello [/INST] response </s>[INST] again [/INST] response </s>
```

```
Usage: ./server -m ... --chat-template monarch
mlabonne/AlphaMonarch-7B
<s>system
test</s>
<s>user
hello</s>
<s>assistant
response</s>
<s>user
again</s>
<s>assistant
response</s>
```

```
Usage: ./server -m ... --chat-template gemma
google/gemma-7b-it
<start_of_turn>user
hello<end_of_turn>
<start_of_turn>model
response<end_of_turn>
<start_of_turn>user
again<end_of_turn>
<start_of_turn>model
response<end_of_turn>
```

```
Usage: ./server -m ... --chat-template orion
<s>Human: hello

Assistant: </s>response</s>Human: again

Assistant: </s>response</s>
```

```
Usage: ./server -m ... --chat-template openchat
openchat/openchat-3.5-0106
<s>GPT4 Correct System: You are a helpful assistant<|end_of_turn|>GPT4 Correct User: Hello<|end_of_turn|>GPT4 Correct Assistant: Hi there<|end_of_turn|>GPT4 Correct User: Who are you<|end_of_turn|>GPT4 Correct Assistant:    I am an assistant   <|end_of_turn|>GPT4 Correct User: Another question<|end_of_turn|>GPT4 Correct Assistant:
```

```
Usage: ./server -m ... --chat-template vicuna
NousResearch/Nous-Capybara-34B
You are a helpful assistant

USER: Hello
ASSISTANT: Hi there</s>
USER: Who are you
ASSISTANT:    I am an assistant   </s>
USER: Another question
ASSISTANT:
```

```
Usage: ./server -m ... --chat-template vicuna-orca
migtissera/Tess-2.0-Yi-34B-200K
SYSTEM: You are a helpful assistant
USER: Hello
ASSISTANT: Hi there</s>
USER: Who are you
ASSISTANT:    I am an assistant   </s>
USER: Another question
ASSISTANT:
```

```
Usage: ./server -m ... --chat-template deepseek
deepseek-ai/deepseek-coder-33b-instruct
You are a helpful assistant### Instruction:
Hello
### Response:
Hi there
<|EOT|>
### Instruction:
Who are you
### Response:
   I am an assistant   
<|EOT|>
### Instruction:
Another question
### Response:
```

```
Usage: ./server -m ... --chat-template command-r
CohereForAI/c4ai-command-r-plus
<|START_OF_TURN_TOKEN|><|SYSTEM_TOKEN|>You are a helpful assistant<|END_OF_TURN_TOKEN|><|START_OF_TURN_TOKEN|><|USER_TOKEN|>Hello<|END_OF_TURN_TOKEN|><|START_OF_TURN_TOKEN|><|CHATBOT_TOKEN|>Hi there<|END_OF_TURN_TOKEN|><|START_OF_TURN_TOKEN|><|USER_TOKEN|>Who are you<|END_OF_TURN_TOKEN|><|START_OF_TURN_TOKEN|><|CHATBOT_TOKEN|>I am an assistant<|END_OF_TURN_TOKEN|><|START_OF_TURN_TOKEN|><|USER_TOKEN|>Another question<|END_OF_TURN_TOKEN|><|START_OF_TURN_TOKEN|><|CHATBOT_TOKEN|>
```

```
Usage: ./server -m ... --chat-template llama3
meta-llama/Meta-Llama-3-8B-Instruct
<|start_header_id|>system<|end_header_id|>\n\nYou are a helpful assistant<|eot_id|><|start_header_id|>user<|end_header_id|>\n\nHello<|eot_id|><|start_header_id|>assistant<|end_header_id|>\n\nHi there<|eot_id|><|start_header_id|>user<|end_header_id|>\n\nWho are you<|eot_id|><|start_header_id|>assistant<|end_header_id|>\n\nI am an assistant<|eot_id|><|start_header_id|>user<|end_header_id|>\n\nAnother question<|eot_id|><|start_header_id|>assistant<|end_header_id|>\n\n
```

此外，我们还支持 zephyr 模板（我无法在 huggingface 上找到它，但在[这个列表](https://github.com/ggerganov/llama.cpp/blob/c8d847d57efdc0f9bbbf881d48c645e151b36fd8/examples/server/public/promptFormats.js)中见过）

```
Usage: ./server -m ... --chat-template zephyr
<|system|>
test<|endoftext|>
<|user|>
hello<|endoftext|>
<|assistant|>
response<|endoftext|>
<|user|>
again<|endoftext|>
<|assistant|>
response<|endoftext|>
```

## 如何添加新模板1. 检查模型在 HuggingFace 的 `tokenizer_config.json` 中的 `chat_template`[(示例)](https://huggingface.co/mistralai/Mistral-7B-Instruct-v0.2/blob/main/tokenizer_config.json#L42)。
	- 如果没有，请先打开一个问题进行讨论。一些较旧的模型实际上早于聊天模板和多轮回复，支持起来会很困难。
2. 使用以下 Python 脚本生成一个测试对话。
	脚本
	from transformers import AutoTokenizer
	VARIANTS\_TO\_TEST \= \[
	    'teknium/OpenHermes-2.5-Mistral-7B',
	    'mistralai/Mistral-7B-Instruct-v0.2',
	    'TheBloke/FusionNet\_34Bx2\_MoE-AWQ',
	    'bofenghuang/vigogne-2-70b-chat',
	    'mlabonne/AlphaMonarch-7B',
	    'google/gemma-7b-it',
	    'OrionStarAI/Orion-14B-Chat',
	    'openbmb/MiniCPM-2B-dpo-fp32',
	    'openchat/openchat-3.5-0106',
	    'deepseek-ai/deepseek-coder-33b-instruct',
	    \# Replace with your model's HuggingFace name
	\]
	HISTORY \= \[
	    { 'role': 'system', 'content': 'You are a helpful assistant' },
	    { 'role': 'user', 'content': 'Hello' },
	    { 'role': 'assistant', 'content': 'Hi there' },
	    { 'role': 'user', 'content': 'Who are you' },
	    { 'role': 'assistant', 'content': '   I am an assistant   ' },
	    { 'role': 'user', 'content': 'Another question' },
	\]
	for variant in VARIANTS\_TO\_TEST:
	    history \= \[m for m in HISTORY\] \# copy
	    if 'Mistral' in variant or 'gemma' in variant:
	        history.pop(0) \# no system prompt for mistral and gemma
	    if 'gemma' in variant:
	        \# GemmaTokenizer is quite buggy, let's hard code the template here
	        GEMMA\_TMLP \= "{% if messages\[0\]\['role'\] == 'system' %}{{ raise\_exception('System role not supported') }}{% endif %}{% for message in messages %}{% if (message\['role'\] == 'user') != (loop.index0 % 2 == 0) %}{{ raise\_exception('Conversation roles must alternate user/assistant/user/assistant/...') }}{% endif %}{% if (message\['role'\] == 'assistant') %}{% set role = 'model' %}{% else %}{% set role = message\['role'\] %}{% endif %}{{ '<start\_of\_turn>' + role + '\\n' + message\['content'\] | trim + '<end\_of\_turn>\\n' }}{% endfor %}{% if add\_generation\_prompt %}{{'<start\_of\_turn>model\\n'}}{% endif %}"
	        print("\\n\----- Gemma -----")
	        output \= AutoTokenizer.from\_pretrained(VARIANTS\_TO\_TEST\[0\]).apply\_chat\_template(history, tokenize\=False, add\_generation\_prompt\=True, chat\_template\=GEMMA\_TMLP)
	        print(output)
	        print("\\n\[Test String\]\\n// google/gemma-7b-it")
	        print(output.replace("\\n", "\\\\n"))
	        print('"' + output.replace("\\n", "\\\\n") + '",')
	    else:
	        print("\\n\----- " + variant + " -----")
	        tokenizer \= AutoTokenizer.from\_pretrained(variant)
	        output \= tokenizer.apply\_chat\_template(history, tokenize\=False, add\_generation\_prompt\=True)
	        print(output)
	        print("\\n\[Test String\]\\n// " + variant)
	        print('"' + output.replace("\\n", "\\\\n") + '",')
3. 将 HuggingFace 中的 `chat_template` 和格式化的文本 `[Test String]` 复制到 [tests/test-chat-template.cpp](https://github.com/ggerganov/llama.cpp/blob/master/tests/test-chat-template.cpp)。
4. 运行 `make tests/test-chat-template`。现在你可以使用这个测试来验证你的模板实现是否与原始版本完全相同。
5. 在 llama.cpp 中实现你的模板（搜索 `llama_chat_apply_template_internal` ）。
	- 这个函数尝试在未指定模板时检测模型的模板。它使用模型的 `chat_template` 元数据，因此请选择一个独特的模式。
6. `make` 并运行测试。重复操作直到输出与原始内容匹配！

## 自定义聊天模板目前，无法使用您自己的聊天模板与 llama.cpp 服务器的 `/chat/completions 功能。`

一种可能的解决方案是使用 `/completions` 端点，并编写您自己的代码（例如，使用 python）在将最终提示传递给 `/completions 之前应用模板。`

TODO: 编写示例 python 代码