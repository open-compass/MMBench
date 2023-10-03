# MMBench

[![evaluation](https://img.shields.io/badge/OpenCompass-Support-royalblue.svg)](https://github.com/internLM/OpenCompass/)

Official repository of "**MMBench: Is Your Multi-modal Model an All-around Player?**"

> **🔥 Attention**<br />
> MMBench is developed by the [OpenCompass Community](https://github.com/open-compass/opencompass), welcome to follow the OpenCompass for more latest evaluation techniques of large model. 

**Download**:  MMBench is splitted into dev and test set, according to a 4:6 ratio. You can download the [**DEV (en)**](https://download.openmmlab.com/mmclassification/datasets/mmbench/mmbench_dev_en_20231003.tsv) set here and the [**TEST (en)**](https://download.openmmlab.com/mmclassification/datasets/mmbench/mmbench_test_en_20231003.tsv) set here. We also provide a verified Chinese-translated version of MMBench ([**DEV (cn)**](https://download.openmmlab.com/mmclassification/datasets/mmbench/mmbench_dev_cn_20231003.tsv) / [**TEST (cn)**](https://download.openmmlab.com/mmclassification/datasets/mmbench/mmbench_test_cn_20231003.tsv)), the users can utilize it to verify the Chinese capability of their VLMs.

**Code**: You can refer to these example [**Code**](https://github.com/open-compass/opencompass/blob/main/configs/multimodal/minigpt_4/README.md) to evaluate your model on MMBench.

## **News**

1. [2023/10/03] We provide a verified Chinese-translated version of MMBench ([**DEV (cn)**](https://download.openmmlab.com/mmclassification/datasets/mmbench/mmbench_dev_cn_20231003.tsv) / [**TEST (cn)**](https://download.openmmlab.com/mmclassification/datasets/mmbench/mmbench_test_cn_20231003.tsv)). Users can utilize it to verify the Chinese capability of their VLMs. We provide an illustration in the figure below. 

![ML](https://opencompass.oss-cn-shanghai.aliyuncs.com/omnimmbench/img/multi_lingual.png)

2. [2023/10/03] We provide a new revised version of **MMBench**, in which we removed around 20+ questions which are noisy or of low quality. The updated version is available here: [**DEV**](https://download.openmmlab.com/mmclassification/datasets/mmbench/mmbench_dev_en_20231003.tsv) / [**TEST**](https://download.openmmlab.com/mmclassification/datasets/mmbench/mmbench_test_en_20231003.tsv). This is a minor change and we find that the evaluation results are basically the same for both versions. Thus you are not required to re-test your model on the new MMBench. 

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

![Capability_Dist](https://opencompass.oss-cn-shanghai.aliyuncs.com/omnimmbench/img/taxonomy2.png)


## Evaluation

In MMBench, we present a new evaluation protocol to yield robust evaluation results at an affordable cost. We use the Circular Evaluation strategy to test if a vision-language model can successfully solve each single problem. The strategy yields much more reliable results than the vanilla evaluation strategy. To deal with the free-form text output of VLMs, we propose to use LLM-based choice extractors to convert the free-form text into a specific choice (A, B, C, etc.).

**The Circular Evaluation Strategy**. To present more robust evaluation results and alleviate the negative impact of noises. We present a new evaluation protocol, called Circular Evaluation, to test if a vision-language model can consistently succeed in solving each single problem. Specifically, for a single-choice problem with N choices, we inference the problem N passes with an VLM. In each pass, we apply circular shifting to the choices and the corresponding answer to generate a new prompt for VLM inference (An example depicted in the below figure). In Circular Evaluation, only if the VLM succeed in all N passes, we say that the VLM succeed in solving this problem. The Circular Evaluation setting is much more challenging than the traditional 1-pass evaluation. For most existing VLMs, it's common to see a 10% ~ 20% drop in Top-1 accuracy with the Circular Evaluation strategy applied.

![Circular](https://opencompass.oss-cn-shanghai.aliyuncs.com/omnimmbench/img/circular_eval.jpg)

**LLM-based Choice Extractors**. As the instruction-following capabilities of VLMs differ a lot, we frequently need to handle the free-form text output from VLMs during evaluation. It's difficult for traditional rule-based matching to extract the choices from the free-form text, thus we resort to LLMs. Given the output of an VLM, we first try rule-based matching to match the output with the choices to save inference cost. Once failed, we try to extract the choice with ChatGPT. We provide ChatGPT with the question, options, model predicitons formated using the prompt template below. Once we obtain the ChatGPT output, we try to use exact matching (previous step) to extract the choice from the GPT output. We attempt up to 3 times to extract the choice. The ChatGPT-based choice extractor exhibits a perfect success rate (> 99.9%) and reasonably good alignment with human experts.

![GPT_Prompt](https://opencompass.oss-cn-shanghai.aliyuncs.com/omnimmbench/img/gpt_prompt.png)

## How To Use?

### Intro to each data sample in MMBench

MMBecnh is split into **dev** and **test** split, and each data sample in each split contains the following field:

```
img: the raw data of an image
question: the question
options: the concated options
category: the leaf category
l2-category: the l2-level category
options_dict: the dict contains all options
index: the unique identifier of current question
context (optional): the context to a question, which is optional.
answer: the target answer to current question. (only exists in the dev split, and is keep confidential for the test split on our evaluation server)
```

### Load MMBench

We provide a code snippet as an example of loading MMBench

```python
import base64
import io
import random

import pandas as pd
from PIL import Image
from torch.utils.data import Dataset

def decode_base64_to_image(base64_string):
    image_data = base64.b64decode(base64_string)
    image = Image.open(io.BytesIO(image_data))
    return image

class MMBenchDataset(Dataset):
    def __init__(self,
                 data_file,
                 sys_prompt='There are several options:'):
        self.df = pd.read_csv(data_file, sep='\t')
        self.sys_prompt = sys_prompt

    def __len__(self):
        return len(self.df)

    def __getitem__(self, idx):
        index = self.df.iloc[idx]['index']
        image = self.df.iloc[idx]['image']
        image = decode_base64_to_image(image)
        question = self.df.iloc[idx]['question']
        answer = self.df.iloc[idx]['answer'] if 'answer' in self.df.iloc[0].keys() else None
        catetory = self.df.iloc[idx]['category']
        l2_catetory = self.df.iloc[idx]['l2-category']

        option_candidate = ['A', 'B', 'C', 'D', 'E']
        options = {
            cand: self.load_from_df(idx, cand)
            for cand in option_candidate
            if self.load_from_df(idx, cand) is not None
        }
        options_prompt = f'{self.sys_prompt}\n'
        for key, item in options.items():
            options_prompt += f'{key}. {item}\n'

        hint = self.load_from_df(idx, 'hint')
        data = {
            'img': image,
            'question': question,
            'answer': answer,
            'options': options_prompt,
            'category': catetory,
            'l2-category': l2_catetory,
            'options_dict': options,
            'index': index,
            'context': hint,
        }
        return data
    
    def load_from_df(self, idx, key):
        if key in self.df.iloc[idx] and not pd.isna(self.df.iloc[idx][key]):
            return self.df.iloc[idx][key]
        else:
            return None
```

### How to construct the inference prompt

```python
if data_sample['context'] is not None:
    prompt = data_sample['context'] + ' ' + data_sample['question'] + ' ' + data_sample['options']
else:
    prompt = data_sample['question'] + ' ' + data_sample['options']
```

For example:

| Question                                  | Options                                                      | Image                                                        |
| ----------------------------------------- | ------------------------------------------------------------ | ------------------------------------------------------------ |
| Which category does this image belong to? | A. Oil Painting<br/>B. Sketch<br/>C. Digital art<br/>D. Photo | <div align="center"><img src="https://github-production-user-asset-6210df.s3.amazonaws.com/34324155/255581681-1364ef43-bd27-4eb5-b9e5-241327b1f920.png" width="30%"></div> |


```python
prompt = """
###Human: Question: Which category does this image belong to?
There are several options: A. Oil Painting, B. Sketch, C. Digital art, D. Photo
###Assistant:
"""
```

You can make custom modifications to the prompt

### How to save results:

You should dump your model's predictions into an excel(.xlsx) file, and this file should contain the following fields:

```
question: the question
A: The first choice
B: The second choice
C: The third choice
D: The fourth choice
prediction: The prediction of your model to current question
category: the leaf category
l2_category: the l2-level category
index: the question index
```

If there are any questions with fewer than four options, simply leave those fields blank.

## Citation

```bibtex
@article{MMBench,
    author  = {Yuan Liu, Haodong Duan, Yuanhan Zhang, Bo Li, Songyang Zhnag, Wangbo Zhao, Yike Yuan, Jiaqi Wang, Conghui He, Ziwei Liu, Kai Chen, Dahua Lin},
    journal = {arXiv:2307.06281},
    title   = {MMBench: Is Your Multi-modal Model an All-around Player?},
    year    = {2023},
}
```
