# MMBench

Official repository of "MMBench: Is Your Multi-modal Model an All-around Player?"

**Download**: You can download the dataset following the instructions [here](https://opencompass.org.cn/mmbench)

**Code**: You can refer to these example codes [here](https://github.com/open-compass/opencompass) to evaluate your model on MMBench.

## About MMBench

In recent years, the field has seen a surge in the development of numerous vision-language (VL) models, such as MiniGPT-4 and LLaVA. These models showcase promising performance in tackling previously challenging tasks. However, effectively evaluating these models' performance has become a primary challenge hindering further advancement in large VL models. Traditional benchmarks like VQAv2 and COCO Caption are widely used to provide quantitative evaluations for VL models but suffer from several shortcomings:

**Dataset Construction**: Dataset Construction: Traditional benchmarks tend to evaluate models based on their performance in various tasks, such as image captioning and visual question answering. Unfortunately, these tasks do not fully capture the fine-grained abilities that a model possesses, potentially impeding future optimization efforts.

**Evaluation Metrics**: Existing evaluation metrics lack robustness. For example, VQAv2 targets a single word or phrase, while many current VL models generate sentences as outputs. Although these sentences may correctly answer the corresponding questions, the existing evaluation metric would assign a Fail score due to an inability to exactly match the given answer. Moreover, recently proposed subjective evaluation metrics, such as that used in mPLUG-Owl, offer comprehensive evaluation of VL models. However, these metrics struggle to scale smoothly due to the significant amount of human labor required for evaluation. Additionally, these evaluations are highly biased and difficult to reproduce.

To address these limitations, we propose a novel approach by defining a set of fine-grained abilities and collecting relevant questions for each ability. We also introduce innovative evaluation strategies to ensure more robust assessment of model predictions. This new benchmark, called MMBench, boasts the following features:

**Data Collection**: To date, we have gathered approximately 3000 questions spanning 20 ability dimensions. Each question is a multiple-choice format with a single correct answer.

**Evaluation**: For a more reliable evaluation, we employ ChatGPT to match a model's prediction with the choices of a question, and then output the corresponding label (A, B, C, D) as the final prediction.

## MMBench Dataset

MMBench is collected from multiple sources, including public datasets and Internet, and currently, contains 2974 multiple-choice questions, covering 20 ability dimensions. We structure the existing 20 ability dimensions into 3 ability dimension levels, from L-1 to L-3. we incorporate Perception and Reasoning as our top-level ability dimensions in our ability taxonomy, referred to as L-1 ability dimension. For L-2 abilities, we derive: 1. Coarse Perception, 2. Fine-grained Single-instance Perception, 3. Fine-grained Cross-instance Perception from L-1 Perception; and 1. Attribute Reasoning, 2. Relation Reasoning, 3. Logic Reasoning from L-1 Reasoning. To make our benchmark as fine-grained as possible to produce informative feedbacks for developing multi-modality models. We further derive L-3 ability dimensions from L-2 ones. To the best of our knowledge, MMBench is the first large-scale evaluation multimodal dataset covering so many ability dimensions.

Compared to previous datasets, MMBench has the following advantages:

**Compared to previous public objective datasets**. MMBench does not evaluate a VL model's performance on a specific task, but rather on a set of fine-grained abilities. This allows us to evaluate a model's performance on a more fine-grained level, and to provide more informative feedbacks for model development.

**Compared to previous subjective datasets**. MMBench is a objective dataset, and the evaluation results are less biased. Moreover, the results on MMBench are guranteed to be reproducible, which is not the case for subjective datasets.

 <img src="https://opencompass.oss-cn-shanghai.aliyuncs.com/omnimmbench/img/taxonomy.jpg" width = "500" height = "500" align=center />


## MMBench Evaluation

In MMBench, we present a new evaluation protocol to yield robust evaluation results at an affordable cost. We use the Circular Evaluation strategy to test if a vision-language model can successfully solve each single problem. The strategy yields much more reliable results than the vanilla evaluation strategy. To deal with the free-form text output of VLMs, we propose to use LLM-based choice extractors to convert the free-form text into a specific choice (A, B, C, etc.).

**The Circular Evaluation Strategy**. To present more robust evaluation results and alleviate the negative impact of noises. We present a new evaluation protocol, called Circular Evaluation, to test if a vision-language model can consistently succeed in solving each single problem. Specifically, for a single-choice problem with N choices, we inference the problem N passes with an VLM. In each pass, we apply circular shifting to the choices and the corresponding answer to generate a new prompt for VLM inference (An example depicted in the below figure). In Circular Evaluation, only if the VLM succeed in all N passes, we say that the VLM succeed in solving this problem. The Circular Evaluation setting is much more challenging than the traditional 1-pass evaluation. For most existing VLMs, it's common to see a 10% ~ 20% drop in Top-1 accuracy with the Circular Evaluation strategy applied.

<img src="https://opencompass.oss-cn-shanghai.aliyuncs.com/omnimmbench/img/circular_eval.jpg" width = "500" height = "100" align=center />

**LLM-based Choice Extractors**. As the instruction-following capabilities of VLMs differ a lot, we frequently need to handle the free-form text output from VLMs during evaluation. It's difficult for traditional rule-based matching to extract the choices from the free-form text, thus we resort to LLMs. Given the output of an VLM, we first try rule-based matching to match the output with the choices to save inference cost. Once failed, we try to extract the choice with ChatGPT. We provide ChatGPT with the question, options, model predicitons formated using the prompt template below. Once we obtain the ChatGPT output, we try to use exact matching (previous step) to extract the choice from the GPT output. We attempt up to 3 times to extract the choice. The ChatGPT-based choice extractor exhibits a perfect success rate (> 99.9%) and reasonably good alignment with human experts.

<img src="https://opencompass.oss-cn-shanghai.aliyuncs.com/omnimmbench/img/gpt_prompt.png" width = "500" height = "200" align=center />