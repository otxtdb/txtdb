---
title: "HuggingFace 模型卡元数据互操作性考虑"
source: "https://github.com/ggml-org/llama.cpp/wiki/HuggingFace-Model-Card-Metadata-Interoperability-Consideration"
author:
  - "[[GitHub]]"
published:
created: 2026-02-27
description: "LLM inference in C/C++. Contribute to ggml-org/llama.cpp development by creating an account on GitHub."
tags:
  - "clippings"
taxonomy: { doc_category: [llama.cpp] }
---



  
以下是按照[与 Hugging Face 讨论协调扩展基础模型来源和数据集来源的处理方式](https://github.com/huggingface/huggingface_hub/issues/2479)所达成的 GGUF KV 键与 Hugging Face 的映射关系。

| **GGUF KV 键** | **Hugging Face 模型卡字段** | **备注** |
| --- | --- | --- |
| `general.name` | `model_name` | 模型名称。 |
| `general.license` | `license` | 许可证标识符。 |
| `general.license.name` | `license_name` | 许可证全称。 |
| `general.license.link` | `license_link` | 许可证文本的 URL。 |
| `general.base_model.{id}.name` | `base_model` | 更简单的字段：HF Hub 上的模型 ID 数组。 |
| `general.base_model.{id}.name` | `base_model_sources[].name` | 扩展：基础模型的详细描述。 |
| `general.base_model.{id}.author` | `base_model_sources[].author` | 父级/基础模型的作者（扩展字段）。 |
| `general.base_model.{id}.version` | `base_model_sources[].version` | 父级/基础模型的版本（扩展字段）。 |
| `general.base_model.{id}.organization` | `base_model_sources[].organization` | 负责父级/基础模型的组织（扩展字段）。 |
| `general.base_model.{id}.description` | `base_model_sources[].description` | 父级/基础模型的描述（扩展字段）。 |
| `general.base_model.{id}.url` | `base_model_sources[].url` | 关于父/基础模型的更多信息 URL（扩展字段）。 |
| `general.base_model.{id}.doi` | `base_model_sources[].doi` | 父/基础模型的 DOI（扩展字段）。 |
| `general.base_model.{id}.uuid` | `base_model_sources[].uuid` | 父/基础模型的 UUID（扩展字段）。 |
| `general.base_model.{id}.repo_url` | `base_model_sources[].repo_url` | 父模型/基础模型的存储库 URL（扩展字段）。 |
| `general.dataset.{id}.name` | `datasets` | 更简单的字段：HF Hub 上的数据集 ID 数组。 |
| `general.dataset.{id}.name` | `dataset_sources[].name` | 扩展：数据集的详细描述。 |
| `general.dataset.{id}.author` | `dataset_sources[].author` | 数据集作者（扩展字段）。 |
| `general.dataset.{id}.version` | `dataset_sources[].version` | 数据集版本（扩展字段）。 |
| `general.dataset.{id}.organization` | `dataset_sources[].organization` | 数据集负责组织（扩展字段）。 |
| `general.dataset.{id}.description` | `dataset_sources[].description` | 数据集描述（扩展字段）。 |
| `general.dataset.{id}.url` | `dataset_sources[].url` | 关于数据集的更多信息 URL（扩展字段）。 |
| `general.dataset.{id}.doi` | `dataset_sources[].doi` | 数据集的 DOI（扩展字段）。 |
| `general.dataset.{id}.uuid` | `dataset_sources[].uuid` | 数据集的 UUID（扩展字段）。 |
| `general.dataset.{id}.repo_url` | `dataset_sources[].repo_url` | 数据集的存储库 URL（扩展字段）。 |
| `general.tags` | `tags` | 描述模型的标签。 |
| `general.languages` | `language` | 模型支持的语言。 |
| `general.description` | *目前尚未明确映射* | 可以包含在模型卡中的自定义"描述"字段中。 |
| `general.url` | *目前尚未明确映射* | 关于模型的进一步信息的一般 URL。 |
| `general.repo_url` | *目前尚未明确映射* | 模型的仓库 URL。 |
| `general.doi` | *目前尚未明确映射* | 模型的 DOI。 |
| `general.uuid` | *目前尚未明确映射* | 模型的 UUID。 |
| `general.size_label` | *目前尚未明确映射* | 可能表示量化或尺寸信息。 |
| `general.quantized_by` | *目前尚未明确映射* | 表示谁执行了量化。 |
| `general.alignment` | *目前尚未明确映射* | 可能表示对齐目标（例如，RLHF 等）。 |
| `general.file_type` | *目前尚未明确映射* | 模型的文件格式（例如，GGUF，Safetensors）。 |

以下是一个示例，展示了上述映射可能的样子：

# Model Card Fields
model\_name: Example Model Six
# Licensing details
license: apache-2.0
license\_name: Apache License Version 2.0, January 2004
license\_link: https://huggingface.co/datasets/choosealicense/licenses/blob/main/markdown/apache-2.0.md
# Simple Model (singular or list of hugging face model ids)
base\_model: stabilityai/stable-diffusion-xl-base-1.0
# Detailed Model Parents (Merges, Pre-tuning, etc...) (list of dicts)
base\_model\_sources:
  - name: GPT-3
    author: OpenAI
    version: '3.0'
    organization: OpenAI
    description:  A large language model capable of performing a wide variety of language tasks.
    url: 'https://openai.com/research/gpt-3'
    doi: 10.5555/gpt3doi123456
    uuid: 123e4567-e89b-12d3-a456-426614174000
    repo\_url: 'https://github.com/openai/gpt-3'
  - name: BERT
    author: Google AI Language
    version: '1.0'
    organization: Google
    description: A transformer-based model pretrained on English to achieve state-of-the-art performance on a range of NLP tasks.
    url: 'https://github.com/google-research/bert'
    doi: 10.5555/bertdoi789012
    uuid: 987e6543-e21a-43f3-a356-527614173999
    repo\_url: 'https://github.com/google-research/bert'
# Simple Dataset (singular or list of hugging face dataset ids)
datasets: common\_voice
# Detailed Model Datasets Used (Training data...) (list of dicts)
dataset\_sources:
  - name: Wikipedia Corpus
    author: Wikimedia Foundation
    version: '2021-06'
    organization: Wikimedia
    description: A dataset comprising the full English Wikipedia, used to train models in a range of natural language tasks.
    url: 'https://dumps.wikimedia.org/enwiki/'
    doi: 10.5555/wikidoi234567
    uuid: 234e5678-f90a-12d3-c567-426614172345
    repo\_url: 'https://github.com/wikimedia/wikipedia-corpus'
  - name: Common Crawl
    author: Common Crawl Foundation
    version: '2021-04'
    organization: Common Crawl
    description: A dataset containing web-crawled data from various domains, providing a broad range of text.
    url: 'https://commoncrawl.org'
    doi: 10.5555/ccdoi345678
    uuid: 345e6789-f90b-34d5-d678-426614173456
    repo\_url: 'https://github.com/commoncrawl/cc-crawl-data'
# Model Content Metadata
tags:
  - text generation
  - transformer
  - llama
  - tiny
  - tiny model
language:
  - en