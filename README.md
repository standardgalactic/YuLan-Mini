<h4 align="center">
    <p>
        <a href="https://github.com/RUC-GSAI/YuLan-Mini/blob/main/README_zh.md">中文</a>| <b>English</b> | <a href="https://github.com/RUC-GSAI/YuLan-Mini/blob/main/README_ja.md">日本語</a> 
    <p>
</h4>

<div align=center>
<img src="assets/YuLan-logo.jpg" width="400px">
<h1>YuLan-Mini: An Open Data-efficient Language Model</h1>
<a href="https://github.com/RUC-GSAI/YuLan-Mini/blob/main/LICENSE"><img src="https://img.shields.io/badge/License-MIT-blue" alt="license"></a>
<a href="https://arxiv.org/abs/2412.17743" target="_blank"><img src=https://img.shields.io/badge/arXiv-b5212f.svg?logo=arxiv></a>
<a href="https://huggingface.co/collections/yulan-team/yulan-mini-676d214b24376739b00d95f3"><img alt="Static Badge" src="https://img.shields.io/badge/%F0%9F%A4%97%20Hugging%20Face-blue?color=8A2BE2"></a>
<a><img src="https://img.shields.io/github/stars/RUC-GSAI/YuLan-Mini"></a>
</div>

YuLan-Mini is a lightweight language model with 2.4 billion parameters. It achieves performance comparable to industry-leading models trained on significantly more data, despite being pre-trained on only 1.08T tokens. The model excels particularly in the domains of **mathematics** and **code**. To facilitate reproducibility, we will open-source the relevant pre-training resources.

---

## Model Downloads 🔗

> Model weights will be uploaded after final preparations.

|  Model  | Context Length | SFT |
|---------|----------------|-----|
| [YuLan-Mini](https://huggingface.co/yulan-team/YuLan-Mini) (Recommended) | 28K | ❎ |
| [YuLan-Mini-2.4B-4K](https://huggingface.co/yulan-team/YuLan-Mini-Intermediate-4K) | 4K | ❎ |
| YuLan-Mini-Instruct | Comming soon | ✅ |

---

## Features 🌟

<div align=center>
<img src="assets/main.png">
</div>

Our pre-training methodology improves training efficiency through three key innovations:

1. an elaborately designed **data pipeline** that combines data cleaning with data schedule strategies;
2. a systematic **optimization method** that can effectively mitigate training instability;
3. an effective **annealing approach** that integrate targeted data selection and long context training.


---
## Behchmarks 🌟

|      Models      | Model Size | # Train Tokens | Context Length | MATH 500 | GSM 8K | Human Eval | MBPP   | RACE Middle | RACE High | RULER  |
|:----------------|----------:|--------------:|--------------:|:--------|:------|:----------|:------|:-----------|:---------|:------|
|     MiniCPM      |    2.6B    |     1.06T      |       4K       |   15.00  |  53.83 |     50.00* |  47.31 |     56.61   |   44.27   |   N/A  |
|      Qwen-2      |    1.5B    |       7T       |      128K      |   22.60  | 46.90* |     34.80* | 46.90* |     55.77   |   43.69   |  60.16 |
|     Qwen2.5      |    0.5B    |      18T       |      128K      |   23.60  | 41.60* |     30.50* | 39.30* |     52.36   |   40.31   |  49.23 |
|     Qwen2.5      |    1.5B    |      18T       |      128K      |   **45.40**  | **68.50\*** |     37.20* | 60.20* |     **58.77**   |   44.33   |  <ins>68.26</ins> |
|     Gemma2       |    2.6B    |       2T       |       8K       |   18.30* | 30.30* |     19.50* | 42.10* |       -     |      -    |   N/A  |
|    StableLM2     |    1.7B    |       2T       |       4K       |     -    |  20.62 |      8.50* |  17.50 |     56.33   |   **45.06**   |   N/A  |
|    SmolLM2       |    1.7B    |      11T       |       8K       |   11.80  |    -   |     23.35  |  45.00 |     55.77   |   43.06   |   N/A  |
|    Llama3.2      |    3.2B    |       9T       |      128K      |    7.40  |    -   |     29.30  |  49.70 |     55.29   |   43.34   |  **77.06** |
|    YuLan-Mini    |    2.4B    |     1.04T      |       4K       |   32.60  |  66.65 |     <ins>61.60</ins>  |  **66.70** |     55.71   |   43.58   |   N/A  |
|    YuLan-Mini    |    2.4B    |     1.08T      |      28K       |  <ins>37.80</ins>  |  <ins>68.46</ins> |    **64.00**  |  <ins>65.90</ins>|     <ins>57.18</ins>   |   <ins>44.57</ins>   |  51.48 |


|      Models      | LAMBADA | MMLU  | CMMLU | CEval | HellaSwag | WinoGrande | StoryCloze | ARC-e | ARC-c |
|:----------------|:-------|:-----|:-----|:-----|:----------|:-----------|:-----------|:-----|:-----|
|   MiniCPM-2.6B   |  61.91  | 53.37 | 48.97 | 48.24 |   67.92    |     65.74   |     78.51   | 55.51 | 43.86 |
|   Qwen2-1.5B     |  64.68  | 55.90 | **70.76** | **71.94** |   66.11    |     66.14   |     77.60   | 62.21 | 42.92 |
|  Qwen2.5-0.5B    |  52.00  | 47.50 | 52.17 | 54.27 |   50.54    |     55.88   |     71.67   | 56.10 | 39.51 |
|  Qwen2.5-1.5B    |  62.12  | <ins>60.71</ins> | <ins>67.82</ins> | <ins>69.05</ins> |   67.18    |     64.48   |     76.80   | **71.51** | <ins>53.41</ins> |
|   Gemma2-2.6B    |    -    | 52.20*|   -   | 28.00*|   <ins>74.60*</ins>   |    **71.50\***   |       -     |   -   | **55.70\***|
| StableLM2-1.7B   |  66.15  | 40.37 | 29.29 | 26.99 |   69.79    |     64.64   |     <ins>78.56</ins>   | 54.00 | 40.78 |
|  SmolLM2-1.7B    |  <ins>67.42</ins>  | 51.91 | 33.46 | 35.10 |   72.96    |     67.40   |     **79.32**   | 44.82 | 35.49 |
|   Llama3.2-3B    |  **69.08**  | **63.40** | 44.44 | 44.49 |   **75.62**    |     <ins>67.48</ins>   |     76.80   | <ins>70.12</ins> | 48.81 |
|    YuLan-Mini    |  64.72  | 51.79 | 48.35 | 51.47 |   68.65    |     67.09   |     76.37   | 69.87 | 50.51 |
|    YuLan-Mini    |  65.67  | 49.10 | 45.45 | 48.23 |   67.22    |     67.24   |     75.89   | 67.47 | 49.32 |


---

## Pre-Training Resources 🔧

To enhance research transparency and reproducibility, we are open-sourcing relevant [pre-training resources](https://github.com/RUC-GSAI/YuLan-Mini/blob/main/pretrain):

<details><summary>1. Pre-training and Evaluation Code</summary>

The pre-training and evaluation code will be released in a future update.
</details>



<details><summary>2. Intermediate Stage Checkpoints</summary>
The intermediate stage checkpoints are released in <a href="https://huggingface.co/collections/yulan-team/yulan-mini-676d214b24376739b00d95f3">YuLan-Mini</a>.

</details>

<details><summary>3. Optimizer States Before Annealing</summary>

<a href="https://huggingface.co/yulan-team/YuLan-Mini-Before-Annealing">YuLan-Mini-Before-Annealing</a>
</details>


<details><summary>4. The Used Open-Source Datasets </summary>

<a href="https://github.com/RUC-GSAI/YuLan-Mini/blob/main/pretrain/datasets-list.md">Used-Datasets-List</a>

</details>

<details><summary>5. Data Distribution for every phase</summary>

<a href="https://github.com/RUC-GSAI/YuLan-Mini/blob/main/pretrain/final.pdf">
  <div align=center>
    <img src="assets/data_distribution_for_every_phase.png">
  </div>
</a>

</details>

<details><summary>6. Synthetic Data</summary>

Data cleaning and synthesis pipeline:
<div align=center>
<img src="https://github.com/RUC-GSAI/YuLan-Mini/blob/main/assets/data-pipeline.png">
</div>

The synthetic data we are using is released in <a href="https://huggingface.co/collections/yulan-team/yulan-mini-676d214b24376739b00d95f3">YuLan-Mini-Datasets</a>

</details>

<details><summary>7. Intermediate Optimizer States</summary>

Intermediate optimizer states will be released in a future update.
</details>


### What you can do with these pre-training resources

1. **Pre-train** your own LLM. You can use [our data](https://huggingface.co/yulan-team/YuLan-Mini-Datasets) and curriculum to train a model that's just as powerful as YuLan-Mini.
2. Perform your own **learning rate annealing**. During the annealing phase, YuLan-Mini's learning ability is at its peak. You can resume training from [the checkpoint before annealing](https://huggingface.co/yulan-team/YuLan-Mini-Before-Annealing) and use your own dataset for learning rate annealing.
3. **Fine-tune** the Instruct version of the LLM. You can use the YuLan-Mini base model to train your own Instruct version.
4. **Training dynamics** research. You can use YuLan-Mini's intermediate checkpoints to explore internal changes during the pre-training process.
5. **Synthesize** your own data. You can use YuLan-Mini's [data pipeline](https://github.com/RUC-GSAI/YuLan-Mini) to clean and generate your own dataset.

---

## Quick Start 💻

Below is a simple example for inference using Huggingface:

**Huggingface Inference Example**
```python
import torch
from transformers import AutoTokenizer, AutoModelForCausalLM

# Load model and tokenizer
tokenizer = AutoTokenizer.from_pretrained("yulan-team/YuLan-Mini")
model = AutoModelForCausalLM.from_pretrained("yulan-team/YuLan-Mini", torch_dtype=torch.bfloat16)

# Input text
input_text = "Renmin University of China is"
inputs = tokenizer(input_text, return_tensors="pt")

# Completion
output = model.generate(inputs["input_ids"], max_new_tokens=100)
print(tokenizer.decode(output[0], skip_special_tokens=True))
```

**vLLM Serve Example**
```bash
vllm serve yulan-team/YuLan-Mini --dtype bfloat16
```

**SGLang Serve Example**
```bash
python -m sglang.launch_server --model-path yulan-team/YuLan-Mini --port 30000 --host 0.0.0.0
```

---

## The Team

YuLan-Mini is developed and maintained by [AI Box, Renmin University of China](http://aibox.ruc.edu.cn/).

## License

- The code in this repository is released under the [MIT License](./LICENSE).
- Policies regarding the use of model weights, intermediate optimizer states, and training data will be announced in future updates.
- Limitations: Despite our efforts to mitigate safety concerns and encourage the generation of ethical and lawful text, the probabilistic nature of language models may still lead to unexpected outputs. For instance, responses might contain bias, discrimination, or other harmful content. Please refrain from disseminating such content. We are not liable for any consequences arising from the spread of harmful information.

## Citation

If you find YuLan-Mini helpful for your research or development, please cite [our technical report](https://arxiv.org/abs/2412.17743):

```
@misc{hu2024yulanmini,
      title={YuLan-Mini: An Open Data-efficient Language Model}, 
      author={Yiwen Hu and Huatong Song and Jia Deng and Jiapeng Wang and Jie Chen and Kun Zhou and Yutao Zhu and Jinhao Jiang and Zican Dong and Wayne Xin Zhao and Ji-Rong Wen},
      year={2024},
      eprint={2412.17743},
      archivePrefix={arXiv},
      primaryClass={cs.CL},
      url={https://arxiv.org/abs/2412.17743}, 
}
```
