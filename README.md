# Data-Centric FinGPT: Open-source for Open Finance. 
[![Downloads](https://static.pepy.tech/badge/fingpt)](https://pepy.tech/project/fingpt)
[![Downloads](https://static.pepy.tech/badge/fingpt/week)](https://pepy.tech/project/fingpt)
[![Python 3.8](https://img.shields.io/badge/python-3.6-blue.svg)](https://www.python.org/downloads/release/python-360/)
[![PyPI](https://img.shields.io/pypi/v/fingpt.svg)](https://pypi.org/project/fingpt/)
![License](https://img.shields.io/github/license/AI4Finance-Foundation/fingpt.svg?color=brightgreen)


<div align="center">
<img align="center" src=figs/logo_transparent_background.png width="40%"/>
</div>

Let us DO NOT expect Wall Street to open-source LLMs nor open APIs, due to FinTech institutes' internal regulations and policies.

[Blueprint of FinGPT](https://arxiv.org/abs/2306.06031)

**Disclaimer: We are sharing codes for academic purposes under the MIT education license. Nothing herein is financial advice, and NOT a recommendation to trade real money. Please use common sense and always first consult a professional before trading or investing.**


[![](https://dcbadge.vercel.app/api/server/trsr8SXpW5)](https://discord.gg/trsr8SXpW5)



## Why FinGPT?

1). Finance is highly dynamic. [BloombergGPT](https://arxiv.org/abs/2303.17564) trained an LLM using a mixture of finance data and general-purpose data, which took about 53 days, at a cost of around **$3M**). It is costly to retrain an LLM model like BloombergGPT every month or every week, thus lightweight adaptation is highly favorable. FinGPT can be fine-tuned swiftly to incorporate new data (the cost falls significantly, less than **$300 per fine-tuning**).

2). Democratizing Internet-scale financial data is critical, say allowing timely updates of the model (monthly or weekly updates) using an automatic data curation pipeline.  BloombergGPT has privileged data access and APIs, while FinGPT presents a more accessible alternative. It prioritizes lightweight adaptation, leveraging the best available open-source LLMs.

3). The key technology is "RLHF (Reinforcement learning from human feedback)", which is missing in BloombergGPT. RLHF enables an LLM model to learn individual preferences (risk-aversion level, investing habits, personalized robo-advisor, etc.), which is the "secret" ingredient of ChatGPT and GPT4.

## FinGPT Demos
* [FinGPT V3 (Updated on 8/4/2023)](./fingpt)
  
  + **FinGPT v3 series are LLMs finetuned with the LoRA method on the News and Tweets sentiment analysis dataset which achieve the best scores on most of the financial sentiment analysis datasets with low cost.**
  + FinGPT v3.1 uses chatglm2-6B as base model; FinGPT v3.2 uses llama2-7b as base model
  + Benchmark Results:
    | Weighted F1   | [BloombergGPT](https://arxiv.org/abs/2303.17564) | [ChatGLM2](https://github.com/THUDM/ChatGLM2-6B) |  [Llama2](https://huggingface.co/meta-llama/Llama-2-7b-chat-hf) |[FinGPT v3.1](https://huggingface.co/oliverwang15/FinGPT_v31_ChatGLM2_Sentiment_Instruction_LoRA_FT) |v3.1.1 (8bit)|v3.1.2 (QLoRA)| [FinGPT v3.2](https://huggingface.co/oliverwang15/FinGPT_v32_Llama2_Sentiment_Instruction_LoRA_FT) |
    | ---------------------- | ------------ | -------- | ---------------- | --------- | ----------------- | ----------------- |----------------- |
    | FPB       | 0.511        | 0.381      | 0.390      | **0.855**      | 0.855           |  0.777          | 0.850          |
    | FiQA-SA   | 0.751        | 0.790      | 0.800      | 0.850          | 0.847            | 0.752      |**0.860**      |
    | TFNS      | -            | 0.189      | 0.296      | 0.875          | 0.879           | 0.828       |**0.894**        |
    | NWGI      | -            | 0.449      | 0.503      | **0.642**      | 0.632            |0.583            |0.636            |
    | Devices   | 512 × A100   | 64 × A100  |  2048 × A100     | 8 × A100     | A100    | A100        |8 × A100        |
    | Time      | 53 days      | 2.5 days   |  21 days     |  2 hours      | 6.47 hours    |   4.15 hours        | 2 hours        |   
    | Cost      | $2.67 million      | $ 14,976   |  $4.23 million    |  $65.6     | $25.88     |  $17.01     |  $65.6     | 
**Cost per GPU hour.** For A100 GPUs, the AWS p4d.24xlarge instance, equipped with 8 A100 GPUs is used as a benchmark to estimate the costs. Note that BloombergGPT also used p4d.24xlarge As of July 11, 2023, the hourly rate for this instance stands at $32.773. Consequently, the estimated cost per GPU hour comes to $32.77 divided by 8, resulting in approximately **$4.10**. With this value as the reference unit price (1 GPU hour). **BloombergGPT estimated cost= 512 x 53 x 24 = 651,264 GPU hours x $4.10 = $2,670,182.40**

  * Reproduce the results by running [benchmarks](./fingpt/FinGPT-v3/benchmark/benchmarks.ipynb), and the detailed tutorial is on the way.
  * Finetune your own FinGPT v3 model with the LoRA method on only an RTX 3090 with this [notebook](./fingpt/FinGPT-v3/training_8bit/train.ipynb) in 8bit or this [notebook](./fingpt/FinGPT-v3/training_int4/train.ipynb) in int4 (QLoRA)
  
* [FinGPT V1](./fingpt)
  + **FinGPT by finetuning ChatGLM2 / Llama2 with LoRA with the market-labeled data for Chinese Market**

## Tutorials
[[Training] Beginner’s Guide to FinGPT: Training with LoRA and ChatGLM2–6B One Notebook, $10 GPU](https://byfintech.medium.com/beginners-guide-to-fingpt-training-with-lora-chatglm2-6b-9eb5ace7fe99)

## Understanding FinGPT: An Educational Blog Series
+ [FinGPT: Powering the Future of Finance with 20 Cutting-Edge Applications
](https://medium.datadriveninvestor.com/fingpt-powering-the-future-of-finance-with-20-cutting-edge-applications-7c4d082ad3d8)
+ [FinGPT I: Why We Built the First Open-Source Large Language Model for Finance
](https://medium.datadriveninvestor.com/fingpt-i-why-we-built-the-first-open-source-large-language-model-for-finance-c01b5517ca)
+ [FinGPT II: Cracking the Financial Sentiment Analysis Task Using Instruction Tuning of General-Purpose Large Language Models
](https://medium.datadriveninvestor.com/fingpt-ii-cracking-the-financial-sentiment-analysis-task-using-instruction-tuning-of-3333bce428c4)


## FinGPT Ecosystem
### FinGPT embraces a full-stack framework for FinLLMs with five layers:
1. **Data source layer**: This layer assures comprehensive market coverage, addressing the temporal sensitivity of financial data through real-time information capture.
2. **Data engineering layer**: Primed for real-time NLP data processing, this layer tackles the inherent challenges of high temporal sensitivity and low signal-to-noise ratio in financial data.
3. **LLMs layer**: Focusing on a range of fine-tuning methodologies such as LoRA, this layer mitigates the highly dynamic nature of financial data, ensuring the model’s relevance and accuracy.
4. **Task layer**: This layer is responsible for executing fundamental tasks. These tasks serve as the benchmarks for performance evaluations and cross-comparisons in the realm of FinLLMs
5. **Application layer**: Showcasing practical applications and demos, this layer highlights the potential capability of FinGPT in the financial sector.

* FinGPT Framework: Open-Source Financial Large Language Models

<div align="center">
<img align="center" src=figs/FinGPT_framework_20231003.png>
</div>

* [FinGPT-RAG](https://github.com/AI4Finance-Foundation/FinGPT/tree/master/fingpt/FinGPT-RAG): We present a retrieval-augmented large language model framework specifically designed for financial sentiment analysis, optimizing information depth and context through external knowledge retrieval, thereby ensuring nuanced predictions.

<div align="center">
<img align="center" src=figs/FinGPT_RAG_framework.png>
</div>

* [FinGPT-FinNLP](https://github.com/AI4Finance-Foundation/FinNLP): FinNLP provides a playground for all people interested in LLMs and NLP in Finance. Here we provide full pipelines for LLM training and finetuning in the field of finance. The full architecture is shown in the following picture. Detail codes and introductions can be found [here](https://github.com/AI4Finance-Foundation/FinNLP). Or you may refer to the [wiki](https://ai4finance-foundation.github.io/FinNLP/)

<div align="center">
<img align="center" src=figs/FinGPT_FinNLP_data_source.png>
</div>

* [FinGPT-Benchmark](https://github.com/AI4Finance-Foundation/FinGPT/tree/master/fingpt/FinGPT-Benchmark): We introduce a novel Instruction Tuning paradigm optimized for open-source Large Language Models (LLMs) in finance, enhancing their adaptability to diverse financial datasets while also facilitating cost-effective, systematic benchmarking from task-specific, multi-task, and zero-shot instruction tuning tasks. 


<div align="center">
<img align="center" src=figs/FinGPT_Benchmark_update1.png>
</div>



## Open-Source Base Model used in the LLMs layer of FinGPT
* Feel free to contribute more open-source base models tailored for various language-specific financial markets.

| Base Model |Pretraining Tokens|Context Length  | Model Advantages |Model Size|Experiment Results |  Applications |
|  ----  |  ----  |  ----  |   ----  |   ----  |  ----  | ----  |
| [Llama-2](https://github.com/facebookresearch/llama)|2 Trillion|4096| Llama-2 excels on English-based market data | [llama-2-7b](https://huggingface.co/meta-llama/Llama-2-7b-hf) and [Llama-2-13b](https://huggingface.co/meta-llama/Llama-2-13b-hf) | llama-2 consistently shows superior fine-tuning results  | Financial Sentiment Analysis, Robo-Advisor |
| [Falcon](https://github.com/falconry/falcon) |1,500B|2048|  Maintains high-quality results while being more resource-efficient | [falcon-7b](https://huggingface.co/tiiuae/falcon-7b) |Good for English market data  | Financial Sentiment Analysis |
| [MPT](https://github.com/mosaicml/llm-foundry) |1T|2048| MPT models can be trained with high throughput efficiency and stable convergence | [mpt-7b](https://huggingface.co/mosaicml/mpt-7b) |Good for English market data  | Financial Sentiment Analysis |
| [Bloom](https://github.com/bigscience-workshop/bigscience/tree/master/train/tr11-176B-ml#readme) |366B|2048| World’s largest open multilingual language model  | [bloom-7b1](https://huggingface.co/bigscience/bloom-7b1) |Good for English market data  | Financial Sentiment Analysis |
| [ChatGLM2](https://github.com/THUDM/ChatGLM2-6B)|1.4T  |32K |Exceptional capability for Chinese language expression| [chatglm2-6b](https://huggingface.co/THUDM/chatglm2-6b) |Shows prowess for Chinese market data  | Financial Sentiment Analysis, Financial Report Summary |
| [Qwen](https://github.com/QwenLM/Qwen-7B)|2.2T  |8k |Fast response and high accuracy| [qwen-7b](https://huggingface.co/tangger/Qwen-7B-Chat) |Effective for Chinese market data  | Financial Sentiment Analysis|
| [InternLM](https://github.com/InternLM/InternLM) |1.8T  |8k |Can flexibly and independently construct workflows |[internlm-7b](https://huggingface.co/internlm/internlm-7b) |Effective for Chinese market data  | Financial Sentiment Analysis |

* Benchmark Results for the above open-source Base Models in the financial sentiment analysis task using the same instruction template for SFT (LoRA):
  | Weighted F1/Acc  |Llama2 |Falcon |  MPT|Bloom |ChatGLM2|Qwen|InternLM |
  | --------- | ----------------- | ------------ | --------------------- | ---------------- | --------------- | ----------------- |----------------- |
  | [FPB](https://huggingface.co/datasets/financial_phrasebank) | 0.863/0.863 | 0.846/0.849  | **0.872**/**0.872**   | 0.810/0.810 | 0.850/0.849 |0.854/0.854| 0.709/0.714 |
  | [FiQA-SA](https://huggingface.co/datasets/pauri32/fiqa-2018)| **0.871**/0.855| 0.840/0.811  | 0.863/0.844 | 0.771/0.753| 0.864/**0.862** | 0.867/0.851  |0.679/0.687 |
  | [TFNS](https://huggingface.co/datasets/zeroshot/twitter-financial-news-sentiment) | 0.896/0.895 | 0.893/0.893 | **0.907**/**0.907** | 0.840/0.840 | 0.859/0.858 | 0.883/0.882|0.729/0.731|
  | [NWGI](https://huggingface.co/datasets/oliverwang15/news_with_gpt_instructions) | **0.649/0.651**   | 0.636/0.638  | 0.640/0.641| 0.573/0.574| 0.619/0.629 |0.638/0.643|0.498/0.503|


## News

+ [Columbia Perspectives on ChatGPT](https://datascience.columbia.edu/news/2023/columbia-perspectives-on-chatgpt/?utm_source=sendinblue&utm_campaign=DSI%20Newsletter%20April%202023&utm_medium=email)
+ [MIT Technology Review] [ChatGPT is about to revolutionize the economy. We need to decide what that looks like](https://www.technologyreview.com/2023/03/25/1070275/chatgpt-revolutionize-economy-decide-what-looks-like/)
+ [BloombergGPT] [BloombergGPT: A Large Language Model for Finance](https://arxiv.org/abs/2303.17564)
+ [Finextra] [ChatGPT and Bing AI to sit as panellists at fintech conference](https://www.finextra.com/newsarticle/41973/chatgpt-and-bing-ai-to-sit-as-panellists-at-fintech-conference)

## ChatGPT at AI4Finance

+ [YouTube video] [I Built a Trading Bot with ChatGPT](https://www.youtube.com/watch?v=fhBw3j_O9LE), combining ChatGPT and FinRL.
+ [Hey, ChatGPT! Explain FinRL code to me!](https://medium.com/@ai4finance/hey-chatgpt-explain-finrl-code-to-me-6a91d612296f)

## Introductory

+ [Sparks of artificial general intelligence: Early experiments with GPT-4](https://arxiv.org/abs/2303.12712)
+ [GPT-4] [GPT-4 Technical Report](https://arxiv.org/abs/2303.08774)
+ [InstructGPT] [Training language models to follow instructions with human feedback](https://openreview.net/forum?id=TG8KACxEON) NeurIPS 2022.

[The Journey of Open AI GPT models](https://medium.com/walmartglobaltech/the-journey-of-open-ai-gpt-models-32d95b7b7fb2).  GPT models explained. Open AI's GPT-1, GPT-2, GPT-3.

+ [GPT-3] [Language models are few-shot learners](https://proceedings.neurips.cc/paper/2020/hash/1457c0d6bfcb4967418bfb8ac142f64a-Abstract.html) NeurIPS 2020.
+ [GPT-2] [Language Models are Unsupervised Multitask Learners](https://cdn.openai.com/better-language-models/language_models_are_unsupervised_multitask_learners.pdf)
+ [GPT-1] [Improving Language Understanding by Generative Pre-Training](https://cdn.openai.com/research-covers/language-unsupervised/language_understanding_paper.pdf)
+ [Transformer] [Attention is All you Need](https://proceedings.neurips.cc/paper/2017/hash/3f5ee243547dee91fbd053c1c4a845aa-Abstract.html) NeurIPS 2017.

## (Financial) Big Data

+ [BloombergGPT] [BloombergGPT: A Large Language Model for Finance](https://arxiv.org/abs/2303.17564)

+ [WHAT’S IN MY AI?](https://lifearchitect.ai/whats-in-my-ai/) A Comprehensive Analysis of Datasets Used to Train GPT-1, GPT-2, GPT-3, GPT-NeoX-20B, Megatron-11B, MT-NLG, and Gopher

+ [FinRL-Meta Repo](https://github.com/AI4Finance-Foundation/FinRL-Meta) and paper [FinRL-Meta: Market Environments and Benchmarks for Data-Driven Financial Reinforcement Learning](https://proceedings.neurips.cc/paper_files/paper/2022/hash/0bf54b80686d2c4dc0808c2e98d430f7-Abstract-Datasets_and_Benchmarks.html). Advances in Neural Information Processing Systems, 2022.

+ [AI4Finance] [FinNLP](https://github.com/AI4Finance-Foundation/FinNLP) Democratizing Internet-scale financial data.

## Interesting Demos

+ [GPT-3 Creative Fiction](https://gwern.net/gpt-3#prompts-as-programming) Creative writing by OpenAI’s GPT-3 model, demonstrating poetry, dialogue, puns, literary parodies, and storytelling. Plus advice on effective GPT-3 prompt programming & avoiding common errors.

## ChatGPT for FinTech

**ChatGPT Trading Bot**
+ [YouTube video] [ChatGPT Trading strategy 20097% returns](https://www.youtube.com/watch?v=unsa_gXPAJ4)
+ [YouTube video] [ChatGPT Coding - Make A Profitable Trading Strategy In Five Minutes!](https://www.youtube.com/watch?v=4SG2884RcDY)
+ [YouTube video] [Easy Automated Live Trading using ChatGPT (+9660.3% hands free)](https://www.youtube.com/watch?v=dIEZVPVOZPQ)
+ [YouTube video] [ChatGPT Trading Strategy 893% Returns](https://www.youtube.com/watch?v=YxjvjK5AD2M)
+ [YouTube video] [ChatGPT 10 Million Trading Strategy](https://www.youtube.com/watch?v=9VPfd08uU4Q)
+ [YouTube video] [ChatGPT: Your Crypto Assistant](https://www.youtube.com/watch?v=LpzeshX6s2w)
+ [YouTube video] [Generate Insane Trading Returns with ChatGPT and TradingView](https://www.youtube.com/watch?v=ekz6ugJE1h0&t=3s)

<!--- 
**(Fast and accurate) Sentiment Analysis**

   GPT-3 can help study customer surveys, social media tweets from customers/users.

   Tweets
+ [Tweet Classifier](https://platform.openai.com/playground/p/default-tweet-classifier?model=text-davinci-003)
+ [Advanced Tweet Classifier](https://platform.openai.com/playground/p/default-adv-tweet-classifier?model=text-davinci-003)

  Financial News
+ [Algorithmic Trading using Sentiment Analysis on News Articles](https://towardsdatascience.com/https-towardsdatascience-com-algorithmic-trading-using-sentiment-analysis-on-news-articles-83db77966704)
+ [Accessing Historical Financial News Headlines with Python](https://python.plainenglish.io/access-historical-financial-news-headlines-with-python-be1b8faaea9f)

**PromptNet** Analogy to ImageNet and WordNet, it is critical to build a PromptNet.

+ [Awesome_Prompting_Papers_in_Computer_Vision](https://github.com/ttengwang/Awesome_Prompting_Papers_in_Computer_Vision)
+ [OpenPrompt](https://github.com/thunlp/OpenPrompt)
+ [promptsource](https://github.com/bigscience-workshop/promptsource)

**Robo-advisor**

**Coding-tutor**

+ [Hey, ChatGPT! Explain FinRL code to me!](https://medium.com/@ai4finance/hey-chatgpt-explain-finrl-code-to-me-6a91d612296f)

**Blogs about ChatGPT for FinTech**

## ChatGPT APIs

Prompting as a new programming paradigm!
+ [Towards Data Science] [GPT-3: Creative Potential of NLP](https://towardsdatascience.com/gpt-3-creative-potential-of-nlp-d5ccae16c1ab)
+ [YouTube video] [OpenAI GPT-3 - Prompt Engineering For Financial NLP](https://www.youtube.com/watch?v=Nl2Cdbao5Ws)

+ [OpenAI API for GPT-3](https://platform.openai.com/docs/models/gpt-3)
+ [ChatGPT-wrapper: python and shell](https://github.com/mmabrouk/chatgpt-wrapper)
+ [OpenAI Examples Library](https://platform.openai.com/examples)
+ [GPT-3 Sandbox (Github)](https://github.com/shreyashankar/gpt3-sandbox) Enable users to create cool web demos using OpenAI GPT-3 API.
+ [Exploring the Capabilities of the ChatGPT API: A Beginner’s Guide](https://levelup.gitconnected.com/exploring-the-capabilities-of-the-chatgpt-api-a-beginners-guide-e9089d49961f)
+ [Reverse engineered ChatGPT API](https://github.com/acheong08/ChatGPT)

**Prompting programming**

## ChatGPT relatives: 

[A Release Timeline](https://github.com/osanseviero/ml_timeline) of many LLMs.

[PaLM](https://arxiv.org/abs/2204.02311)

[Chincella](https://arxiv.org/abs/2203.15556)

Interesting evaluations:
+ [RLHF for pretraining](https://arxiv.org/abs/2302.08582)

+ [Compare ChatGPT with GPT3.5](https://arxiv.org/pdf/2302.06476.pdf)

+ [Is ChatGPT A Good Translator? A Preliminary Study](https://arxiv.org/pdf/2301.08745.pdf)

+ [A Multitask, Multilingual, Multimodal Evaluation of ChatGPT
on Reasoning, Hallucination, and Interactivity](https://arxiv.org/pdf/2302.04023.pdf)

[YouTube video] [Physics Solution: ChatGPT vs. Google](https://www.youtube.com/watch?v=x4dIx9VYQoM)
---> 

## Citing FinGPT
```
@article{yang2023fingpt,
  title={FinGPT: Open-Source Financial Large Language Models},
  author={Yang, Hongyang and Liu, Xiao-Yang and Wang, Christina Dan},
  journal={FinLLM Symposium at IJCAI 2023},
  year={2023}
}
@article{zhang2023instructfingpt,
      title={Instruct-FinGPT: Financial Sentiment Analysis by Instruction Tuning of General-Purpose Large Language Models}, 
      author={Boyu Zhang and Hongyang Yang and Xiao-Yang Liu},
      journal={FinLLM Symposium at IJCAI 2023},
      year={2023}
}
@article{zhang2023fingptrag,
  title={Enhancing Financial Sentiment Analysis via Retrieval Augmented Large Language Models},
  author={Zhang, Boyu and Yang, Hongyang and Zhou, tianyu and Babar, Ali and Liu, Xiao-Yang},
 journal = {ACM International Conference on AI in Finance (ICAIF)},
  year={2023}
}
```

<div align="center">
<a href="https://finllm.github.io/workshop/#/fcb" target="_blank">
<img align="center" src=figs/fingpt_best_presentation.png width="65%">
</div>

## Links

+ [LLM Survey](https://github.com/RUCAIBox/LLMSurvey)
+ [Awesome GPT-3 Examples](https://github.com/elyase/awesome-gpt3)
