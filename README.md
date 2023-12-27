# MMBench

[![evaluation](https://img.shields.io/badge/OpenCompass-Support-royalblue.svg)](https://github.com/internLM/OpenCompass/)

Official repository of ["**MMBench: Is Your Multi-modal Model an All-around Player?**"](https://arxiv.org/abs/2307.06281)

> **🔥 Attention**<br>
> MMBench is developed by the [**OpenCompass Community**](https://github.com/open-compass/opencompass), welcome to follow the OpenCompass for more latest evaluation techniques of large model. 

**Download**:  MMBench is a collection of benchmarks to evaluate the multi-modal understanding capability of large vision language models (LVLMs). The table below list the information of all benchmarks included in MMBench as well as their download links. 

| Name              | Split | Language | # Questions | Comment                                      | Download Link                                                |
| ----------------- | ----- | -------- | ----------- | -------------------------------------------- | ------------------------------------------------------------ |
| MMBench-Dev       | Dev   | EN       | 1164        | The Dev Split of MMBench                     | **[Download](http://opencompass.openxlab.space/utils/VLMEval/MMBench_DEV_EN.tsv)** |
| MMBench-Test      | Test  | EN       | 1784        | The Test Split of MMBench                    | **[Download](http://opencompass.openxlab.space/utils/VLMEval/MMBench_TEST_EN.tsv)** |
| MMBench-Dev (cn)  | Dev   | CN       | 1164        | Chinese Version of MMBench-Dev               | **[Download](http://opencompass.openxlab.space/utils/VLMEval/MMBench_DEV_CN.tsv)** |
| MMBench-Test (cn) | Test  | CN       | 1784        | Chinese Version of MMBench-Test              | **[Download](http://opencompass.openxlab.space/utils/VLMEval/MMBench_TEST_CN.tsv)** |
| CCBench           | Dev   | CN       | 510         | A Benchmark on Chinese Culture Related Stuff | **[Download](http://opencompass.openxlab.space/utils/VLMEval/CCBench.tsv)** |

**Visualization**: You can visualize data samples of benchmarks in MMBench in [**Visualization**](/samples/README.md). 

**Evaluation**: Please use our official evaluation toolkit [**VLMEvalKit**](https://github.com/open-compass/VLMEvalKit) for MMBench evaluation. 

## **News**

1. [2023/12/26] We have updated **CCBench** and removed noisy testing samples, the new version can be downloaded here [**Download**](http://opencompass.openxlab.space/utils/VLMEval/CCBench.tsv). The leaderboard is updated accordingly. 

2. [2023/10/23] We provide a new benchmark named **CCBench**, which is a multi-modal benchmark in the domain of Chinese Culture.

3. [2023/10/03] We provide a verified **Chinese**-translated version of MMBench. Users can utilize it to verify the Chinese capability of their VLMs. We provide an illustration in the figure below. 

<div align="center">
<img src="https://opencompass.oss-cn-shanghai.aliyuncs.com/omnimmbench/img/multi_lingual.png" width="60%">
</div>

## About MMBench

In recent years, the field has seen a surge in the development of numerous vision-language (VL) models, such as MiniGPT-4 and LLaVA. These models showcase promising performance in tackling previously challenging tasks. However, effectively evaluating these models' performance has become a primary challenge hindering further advancement in large VL models. Traditional benchmarks like VQAv2 and COCO Caption are widely used to provide quantitative evaluations for VL models but suffer from several shortcomings:

**Dataset Construction**: Dataset Construction: Traditional benchmarks tend to evaluate models based on their performance in various tasks, such as image captioning and visual question answering. Unfortunately, these tasks do not fully capture the fine-grained abilities that a model possesses, potentially impeding future optimization efforts.

**Evaluation Metrics**: Existing evaluation metrics lack robustness. For example, VQAv2 targets a single word or phrase, while many current VL models generate sentences as outputs. Although these sentences may correctly answer the corresponding questions, the existing evaluation metric would assign a Fail score due to an inability to exactly match the given answer. Moreover, recently proposed subjective evaluation metrics, such as that used in mPLUG-Owl, offer comprehensive evaluation of VL models. However, these metrics struggle to scale smoothly due to the significant amount of human labor required for evaluation. Additionally, these evaluations are highly biased and difficult to reproduce.

To address these limitations, we propose a novel approach by defining a set of fine-grained abilities and collecting relevant questions for each ability. We also introduce innovative evaluation strategies to ensure more robust assessment of model predictions. This new benchmark, called MMBench, boasts the following features:

**Data Collection**: To date, we have gathered approximately 3000 questions spanning 20 ability dimensions. Each question is a multiple-choice format with a single correct answer.

**Evaluation**: For a more reliable evaluation, we employ ChatGPT to match a model's prediction with the choices of a question, and then output the corresponding label (A, B, C, D) as the final prediction.

## Dataset

MMBench is collected from multiple sources, including public datasets and Internet, and currently, contains 2974 multiple-choice questions, covering 20 ability dimensions. We structure the existing 20 ability dimensions into 3 ability dimension levels, from L-1 to L-3. we incorporate Perception and Reasoning as our top-level ability dimensions in our ability taxonomy, referred to as L-1 ability dimension. For L-2 abilities, we derive: 1. Coarse Perception, 2. Fine-grained Single-instance Perception, 3. Fine-grained Cross-instance Perception from L-1 Perception; and 1. Attribute Reasoning, 2. Relation Reasoning, 3. Logic Reasoning from L-1 Reasoning. To make our benchmark as fine-grained as possible to produce informative feedbacks for developing multi-modality models. We further derive L-3 ability dimensions from L-2 ones. To the best of our knowledge, MMBench is the first large-scale evaluation multimodal dataset covering so many ability dimensions.

Compared to previous datasets, MMBench has the following advantages:

**Compared to previous public objective datasets**. MMBench does not evaluate a VL model's performance on a specific task, but rather on a set of fine-grained abilities. This allows us to evaluate a model's performance on a more fine-grained level, and to provide more informative feedbacks for model development.

**Compared to previous subjective datasets**. MMBench is a objective dataset, and the evaluation results are less biased. Moreover, the results on MMBench are guranteed to be reproducible, which is not the case for subjective datasets.

<div align="center">
<img src="https://opencompass.oss-cn-shanghai.aliyuncs.com/omnimmbench/img/taxonomy2.png" width="50%">
</div>


## Evaluation

In MMBench, we present a new evaluation protocol to yield robust evaluation results at an affordable cost. We use the Circular Evaluation strategy to test if a vision-language model can successfully solve each single problem. The strategy yields much more reliable results than the vanilla evaluation strategy. To deal with the free-form text output of VLMs, we propose to use LLM-based choice extractors to convert the free-form text into a specific choice (A, B, C, etc.).

**The Circular Evaluation Strategy**. To present more robust evaluation results and alleviate the negative impact of noises. We present a new evaluation protocol, called Circular Evaluation, to test if a vision-language model can consistently succeed in solving each single problem. Specifically, for a single-choice problem with N choices, we inference the problem N passes with an VLM. In each pass, we apply circular shifting to the choices and the corresponding answer to generate a new prompt for VLM inference (An example depicted in the below figure). In Circular Evaluation, only if the VLM succeed in all N passes, we say that the VLM succeed in solving this problem. The Circular Evaluation setting is much more challenging than the traditional 1-pass evaluation. For most existing VLMs, it's common to see a 10% ~ 20% drop in Top-1 accuracy with the Circular Evaluation strategy applied.

<div align="center">
<img src="https://opencompass.oss-cn-shanghai.aliyuncs.com/omnimmbench/img/circular_eval.jpg" width="100%">
</div>

**LLM-based Choice Extractors**. As the instruction-following capabilities of VLMs differ a lot, we frequently need to handle the free-form text output from VLMs during evaluation. It's difficult for traditional rule-based matching to extract the choices from the free-form text, thus we resort to LLMs. Given the output of an VLM, we first try rule-based matching to match the output with the choices to save inference cost. Once failed, we try to extract the choice with ChatGPT. We provide ChatGPT with the question, options, model predicitons formated using the prompt template below. Once we obtain the ChatGPT output, we try to use exact matching (previous step) to extract the choice from the GPT output. We attempt up to 3 times to extract the choice. The ChatGPT-based choice extractor exhibits a perfect success rate (> 99.9%) and reasonably good alignment with human experts.

<div align="center">
<img src="https://opencompass.oss-cn-shanghai.aliyuncs.com/omnimmbench/img/gpt_prompt.png" width="70%">
</div>

## How To Use?

Please use our official evaluation toolkit [**VLMEvalKit**](https://github.com/open-compass/VLMEvalKit) for MMBench evaluation. Here we present some scripts for loading and browsing MMBench (you need to install VLMEvalKit first).

```python
from vlmeval.utils import TSVDataset
from vlmeval.smp import mmqa_display
# Load MMBench-DEV-EN
dataset = TSVDataset('MMBench-DEV-EN')
# Display Samples
dataset.display(0)
""" 
Output: <image>
QUESTION. Identify the question that Madelyn and Tucker's experiment can best answer.
HINT. The passage below describes an experiment. Read the passage and then follow the instructions below.

Madelyn applied a thin layer of wax to the underside of her snowboard and rode the board straight down a hill. Then, she removed the wax and rode the snowboard straight down the hill again. She repeated the rides four more times, alternating whether she rode with a thin layer of wax on the board or not. Her friend Tucker timed each ride. Madelyn and Tucker calculated the average time it took to slide straight down the hill on the snowboard with wax compared to the average time on the snowboard without wax.
Figure: snowboarding down a hill.
A. Does Madelyn's snowboard slide down a hill in less time when it has a thin layer of wax or a thick layer of wax?
B. Does Madelyn's snowboard slide down a hill in less time when it has a layer of wax or when it does not have a layer of wax?
ANSWER. B
CATEGORY. identity_reasoning
SOURCE. scienceqa
L2-CATEGORY. attribute_reasoning
SPLIT. dev
"""
```

**To infer the results:**

```bash
# Take llava_v1.5_7b as an example
# To evaluate your own model, replace `llava_v1.5_7b` with the name of your implemented model
python run.py --model llava_v1.5_7b --data MMBench_TEST_EN --mode infer
```

The command will output an excel file: `{model_name}/{model_name}_{dataset_name}.xlsx`. For **MMBench-TEST-CN/EN**, you can submit the file to https://mmbench.opencompass.org.cn/mmbench-submission to obtain the evaluation accuracies. 

## Citation

```bibtex
@article{MMBench,
    author  = {Yuan Liu, Haodong Duan, Yuanhan Zhang, Bo Li, Songyang Zhnag, Wangbo Zhao, Yike Yuan, Jiaqi Wang, Conghui He, Ziwei Liu, Kai Chen, Dahua Lin},
    journal = {arXiv:2307.06281},
    title   = {MMBench: Is Your Multi-modal Model an All-around Player?},
    year    = {2023},
}
```
