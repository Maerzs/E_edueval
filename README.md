# EduEval Benchmark 



## Overview
EduEval is a comprehensive tool for generating and evaluating model outputs in the educational domain, supporting various model access methods and evaluation task types.

## Directory Structure

```
Edueval/
├── code/
│   ├── generate/            # Model generation modules
│   │   ├── model_gen.py     # Base generator class
│   │   ├── qwen_gen.py      # Qwen model generator
│   │   ├── glm_gen.py       # GLM model generator
│   │   ├── baichuan_gen.py  # Baichuan model generator
│   │   └── llama_gen.py     # Llama model generator
│   ├── evaluate/            # Evaluation modules
│   │   └── evaluator.py     # Evaluation metrics and methods
│   ├── prompt_builder.py    # Utilities for building prompts
│   └── main.py              # Main entry point
├── Edata/                   # English educational data
│   ├── Memory/              # Knowledge recall tasks
│   ├── Understanding/       # Reading comprehension tasks
│   ├── Application/         # Application tasks
│   ├── Reasoning/           # Logical reasoning tasks
│   ├── Creativity/          # Creative tasks
│   └── Ethics/              # Ethical reasoning tasks
└── README.md                # This documentation
```

## Framework Components

### Generation Module

The generation module is responsible for running language models on educational tasks. It includes:

- **ModelGenerator (model_gen.py)**: Base class that handles the core functionality for all model types
- **QwenGenerator (qwen_gen.py)**: Specialized for Qwen models (Qwen-7B, Qwen-14B)
- **GLMGenerator (glm_gen.py)**: Specialized for GLM models (ChatGLM, GLM-3)
- **BaichuanGenerator (baichuan_gen.py)**: Specialized for Baichuan models
- **LlamaGenerator (llama_gen.py)**: Specialized for Llama models (Llama-2, Llama-3, Vicuna)

Each generator handles model-specific prompt formatting, output processing, and answer extraction.

### Evaluation Module

The evaluation module assesses model outputs against reference answers, including:

- Accuracy metrics for multiple-choice questions
- BLEU/ROUGE scores for open-ended questions
- Custom scoring for various task types

### Prompt Building

The framework includes utilities for constructing appropriate prompts based on task types:

- Multiple-choice prompts
- Short answer prompts
- Essay prompts
- Reading comprehension prompts

## Supported Models

EduEval has been tested with the following models (ranked by zero-shot performance):

1. **Spark-X1** (81.1% average accuracy)
2. **Qwen-plus** (77.7% average accuracy)
3. **Qwen-72B** (75.0% average accuracy)
4. **DeepseekR1-32B** (74.8% average accuracy)
5. **GPT-4o** (71.0% average accuracy)
6. **Yi-34B** (69.8% average accuracy)
7. **Qwen-14B-Chat** (68.1% average accuracy)
8. **GLM4-9B-Chat** (67.6% average accuracy)
9. **Qwen-7B** (60.8% average accuracy)
10. **Yi-6B** (57.9% average accuracy)
11. **EduChat-sft-002-13b** (53.8% average accuracy)
12. **LLaMA3-8B** (50.3% average accuracy)
13. **Baichuan-13b** (48.7% average accuracy)
14. **LLaMA2-Chinese-13B** (39.3% average accuracy)

The framework supports various LLM architectures through specialized generators:

- **Qwen models**: Qwen-plus, Qwen-72B, Qwen-14B-Chat, Qwen-7B
- **GLM models**: GLM4-9B-Chat
- **Baichuan/Yi models**: Yi-34B, Yi-6B, Baichuan-13b
- **Llama models**: LLaMA3-8B, LLaMA2-Chinese-13B
- **Other models**: Spark-X1, DeepseekR1-32B, GPT-4o, EduChat-sft-002-13b

## Supported Task Types

The framework supports six dimensions of educational tasks:

1. **Memory**: Basic knowledge recall and memorization
2. **Understanding**: Reading comprehension and interpretation
3. **Application**: Applying knowledge to solve problems
4. **Reasoning**: Logical reasoning and inference
5. **Creativity**: Creative problem-solving and generation
6. **Ethics**: Ethical reasoning and decision-making

## Experimental Results

### Zero-shot Performance

The following tables present the zero-shot performance results of various models on the educational dimensions evaluated using the EduEval framework:

#### Memory, Understanding, and Application Dimensions

| Model | Memory |  |  | Understanding |  |  |  |  | Application |  |  |  |  |
|-------|--------|--------|--------|--------------|--------|--------|--------|--------|------------|--------|--------|--------|--------|
|  | 1-1 | 1-2 | 1-3 | 2-1 | 2-2 | 2-3 | 2-4* | 2-5* | 3-1 | 3-2 | 3-3 | 3-4 | 3-5† |
| Spark-X1 | **92.5** | **86.2** | **91.0** | **93.1** | **86.6** | 88.4 | 48.9 | 50.5 | 27.8 | **95.4** | **87.6** | **91.0** | 43.175 |
| Qwen-plus | 81.8 | 82.0 | 89.2 | 89.4 | 85.3 | **90.9** | 47.7 | 50.6 | 24.8 | 75.9 | 83.2 | 79.0 | 12.240 |
| Qwen-72B | 79.8 | 78.8 | 89.3 | 85.7 | 81.4 | 86.8 | 48.4 | 50.1 | 24.8 | 74.4 | 80.9 | 72.1 | 32.815 |
| DeepseekR1-32B | 78.5 | 80.0 | 89.0 | 86.8 | 83.4 | 82.0 | 47.8 | 50.7 | 18.1 | 79.3 | 84.8 | 83.4 | 21.410 |
| GPT-4o | 72.0 | 74.9 | 81.2 | 82.2 | 81.3 | 80.7 | 48.5 | 51.3 | **28.2** | 58.9 | 76.6 | 58.3 | **9.013** |
| Yi-34B | 74.3 | 70.9 | 79.8 | 79.0 | 78.0 | 80.2 | 49.3 | 51.3 | 17.3 | 60.8 | 77.0 | 60.8 | 28.528 |
| Qwen-14B-Chat | 71.0 | 73.0 | 78.8 | 81.9 | 77.6 | 78.2 | **49.8** | **51.8** | 17.1 | 50.2 | 76.6 | 54.8 | 34.109 |
| GLM4-9B-Chat | 67.8 | 72.4 | 77.4 | 77.4 | 78.8 | 80.7 | 49.7 | 50.8 | 22.2 | 52.8 | 73.6 | 61.0 | 28.260 |
| Qwen-7B | 60.0 | 62.3 | 63.0 | 68.7 | 68.4 | 68.9 | 48.8 | 51.3 | 15.5 | 44.3 | 66.7 | 49.5 | 35.814 |
| Yi-6B | 56.8 | 61.0 | 60.4 | 62.2 | 62.5 | 61.4 | 47.8 | 51.1 | 14.9 | 41.7 | 63.4 | 47.5 | 35.742 |
| EduChat-sft-002-13b | 51.1 | 51.2 | 52.8 | 59.7 | 58.7 | 59.1 | 48.9 | 49.9 | 20.5 | 35.7 | 56.8 | 39.9 | 13.3 |
| LLaMA3-8B | 41.0 | 43.8 | 44.3 | 48.1 | 47.5 | 47.8 | 42.4 | 46.2 | 10.1 | 32.4 | 48.5 | 34.1 | 12.476 |
| Baichuan-13b | 39.1 | 45.9 | 39.9 | 49.4 | 48.1 | 46.1 | 49.1 | 50.1 | 11.5 | 33.9 | 48.3 | 38.2 | 33.393 |
| LLaMA2-Chinese-13B | 28.1 | 34.2 | 32.5 | 32.5 | 32.2 | 33.0 | 47.1 | 50.8 | 16.4 | 27.7 | 34.6 | 26.2 | 26.298 |

*\* Tasks 2-4 and 2-5 are evaluated using Rouge-L metric*  
*† Task 3-5 uses RMSE metric (lower is better)*  
*All other tasks are evaluated using accuracy*

#### Reasoning, Creation, and Ethics Dimensions

| Model | Reasoning |  |  |  | Creation* |  |  | Ethics |  |  |  | Average | Rank |
|-------|-----------|--------|--------|--------|----------|--------|--------|--------|--------|--------|--------|---------|------|
|  | 4-1 | 4-2 | 4-3 | 4-4 | 5-1 | 5-2 | 5-3 | 6-1 | 6-2 | 6-3 | 6-4 |  |  |
| Spark-X1 | **78.8** | **90.6** | **93.6** | **88.0** | 88.3 | 85.9 | **88.7** | 74.4 | 81.0 | 77.8 | 79.8 | **81.1** | **1** |
| Qwen-plus | 72.6 | 69.2 | 88.4 | 85.8 | 86.3 | 87.0 | 86.4 | 80.0 | **85.4** | **83.4** | **85.4** | 77.7 | 2 |
| Qwen-72B | 69.6 | 65.7 | 84.6 | 78.8 | 87.8 | **90.4** | 80.0 | 78.7 | 79.3 | 78.2 | 78.3 | 75.0 | 3 |
| DeepseekR1-32B | 67.9 | 75.4 | 66.7 | 78.6 | 85.5 | 86.3 | 81.1 | 76.8 | 79.2 | 78.8 | 80.2 | 74.8 | 4 |
| GPT-4o | 65.4 | 54.7 | 71.8 | 71.6 | **89.4** | 84.6 | 84.9 | 76.4 | 81.4 | 78.6 | 80.0 | 71.0 | 5 |
| Yi-34B | 58.1 | 56.0 | 78.8 | 66.0 | 83.9 | 90.0 | 78.7 | 75.6 | 81.2 | 79.8 | 79.2 | 69.8 | 6 |
| Qwen-14B-Chat | 40.0 | 50.0 | 78.4 | 66.2 | 77.9 | 88.0 | 72.1 | **84.0** | 84.2 | 81.6 | 80.0 | 68.1 | 7 |
| GLM4-9B-Chat | 59.4 | 46.8 | 76.6 | 68.0 | 77.0 | 86.5 | 74.8 | 72.0 | 79.2 | 74.6 | 74.4 | 67.6 | 8 |
| Qwen-7B | 38.4 | 44.8 | 66.8 | 60.6 | 80.7 | 87.8 | 71.4 | 69.6 | 72.6 | 71.6 | 73.8 | 60.8 | 9 |
| Yi-6B | 40.6 | 41.4 | 60.4 | 53.5 | 74.0 | 88.4 | 77.0 | 70.8 | 63.2 | 69.5 | 62.9 | 57.9 | 10 |
| EduChat-sft-002-13b | 31.8 | 36.5 | 49.5 | 50.9 | 71.2 | 84.6 | 67.5 | 69.6 | 78.2 | 73.2 | 73.4 | 53.8 | 11 |
| LLaMA3-8B | 39.0 | 34.1 | 39.1 | 43.1 | 85.5 | 86.4 | 77.7 | 70.0 | 68.8 | 69.0 | 65.0 | 50.3 | 12 |
| Baichuan-13b | 35.3 | 29.7 | 41.0 | 42.3 | 70.0 | 85.8 | 66.6 | 62.0 | 61.8 | 64.2 | 61.8 | 48.7 | 13 |
| LLaMA2-Chinese-13B | 25.7 | 25.9 | 21.8 | 23.9 | 63.0 | 85.4 | 55.7 | 59.5 | 49.8 | 47.8 | 50.6 | 39.3 | 14 |

*\* Creativity tasks (5-1, 5-2, 5-3) use GPT-based evaluation*  
*All other tasks are evaluated using accuracy*

### Few-shot Performance

The following tables present the few-shot performance results of various models on the educational dimensions:

#### Memory, Understanding, and Application Dimensions (Few-shot)

| Model | Memory |  |  | Understanding |  |  |  |  | Application |  |  |  |  |
|-------|--------|--------|--------|--------------|--------|--------|--------|--------|------------|--------|--------|--------|--------|
|  | 1-1 | 1-2 | 1-3 | 2-1 | 2-2 | 2-3 | 2-4* | 2-5* | 3-1 | 3-2 | 3-3 | 3-4 | 3-5† |
| Spark-X1 | **91.3** | **85.2** | **91.2** | **92.7** | **86.6** | **89.8** | **48.6** | **50.4** | **26.6** | **94.6** | **85.2** | **83.6** | **23.0** |
| Qwen-plus | 82.2 | 80.6 | 89.2 | 88.8 | 84.0 | 91.0 | 48.9 | 51.0 | 27.4 | 78.3 | 83.8 | 76.8 | 8.7 |
| GPT-4o | 72.7 | 74.3 | 79.8 | 83.3 | 82.4 | 81.2 | 49.2 | 51.7 | 29.1 | 62.7 | 76.8 | 58.7 | 8.9 |
| DeepseekR1-32B | 79.3 | 60.0 | 86.6 | 85.9 | 53.1 | 84.6 | 47.5 | 50.5 | 21.4 | 68.0 | 52.8 | 75.8 | 20.6 |
| Qwen-72B | 78.3 | 75.6 | 88.6 | 84.9 | 79.0 | 85.4 | 47.6 | 51.6 | 25.4 | 80.9 | 78.6 | 74.9 | 15.4 |
| Qwen-14B-Chat | 69.3 | 71.9 | 79.4 | 79.9 | 77.7 | 82.9 | 49.8 | 51.6 | 20.2 | 53.5 | 72.9 | 60.6 | 10.6 |
| GLM4-9B-Chat | 62.1 | 69.3 | 73.6 | 65.7 | 73.8 | 75.5 | 49.1 | 48.2 | 19.3 | 64.0 | 70.5 | 62.4 | 8.4 |
| Yi-34B | 66.3 | 65.5 | 71.3 | 77.5 | 75.0 | 76.4 | 48.8 | 50.7 | 18.9 | 54.5 | 71.1 | 54.5 | 9.2 |
| Qwen-7B | 54.9 | 50.0 | 55.6 | 65.7 | 63.9 | 64.1 | 48.7 | 51.2 | 13.2 | 39.9 | 62.2 | 45.8 | 13.8 |
| EduChat-sft-002-13b | 51.6 | 52.4 | 52.1 | 56.8 | 59.9 | 59.7 | 47.9 | 42.9 | 23.5 | 34.2 | 59.8 | 38.8 | 12.1 |
| Yi-6B | 48.8 | 56.9 | 48.3 | 52.2 | 50.4 | 41.3 | 48.7 | 50.8 | 12.9 | 50.8 | 50.4 | 43.5 | 29.3 |
| Baichuan-13b | 39.5 | 47.2 | 39.9 | 46.0 | 49.7 | 49.9 | 47.3 | 44.0 | 17.8 | 31.7 | 52.5 | 37.7 | 13.6 |
| LLaMA3-8B | 38.0 | 42.6 | 39.0 | 47.5 | 41.6 | 47.9 | 43.4 | 46.0 | 14.5 | 43.1 | 48.9 | 37.8 | 16.4 |
| LLaMA2-Chinese-13B | 35.0 | 34.7 | 29.0 | 32.0 | 29.8 | 31.9 | 47.4 | 50.4 | 11.6 | 20.6 | 30.6 | 26.0 | 21.2 |

*\* Tasks 2-4 and 2-5 are evaluated using Rouge-L metric*  
*† Task 3-5 uses RMSE metric (lower is better)*  
*All other tasks are evaluated using accuracy*

#### Reasoning, Creation, and Ethics Dimensions (Few-shot)

| Model | Reasoning |  |  |  | Creation* |  |  | Ethics |  |  |  | Average | Rank |
|-------|-----------|--------|--------|--------|----------|--------|--------|--------|--------|--------|--------|---------|------|
|  | 4-1 | 4-2 | 4-3 | 4-4 | 5-1 | 5-2 | 5-3 | 6-1 | 6-2 | 6-3 | 6-4 |  |  |
| Spark-X1 | **77.8** | **89.1** | **94.2** | **87.6** | 74.0 | 43.6 | 54.5 | **81.2** | **84.2** | **80.0** | **82.4** | **77.4** | **1** |
| Qwen-plus | 70.8 | 69.7 | 87.2 | 84.8 | **78.3** | **59.0** | **64.8** | 82.0 | 89.4 | 87.4 | 87.4 | 75.8 | 2 |
| Qwen-72B | 69.4 | 70.3 | 86.0 | 79.0 | 79.7 | 35.9 | 62.2 | 79.6 | 82.1 | 80.6 | 81.8 | 72.1 | 3 |
| DeepseekR1-32B | 61.0 | 61.2 | 88.1 | 77.9 | 83.5 | 52.4 | 70.1 | 81.2 | 83.6 | 82.0 | 83.4 | 69.5 | 4 |
| GPT-4o | 64.7 | 52.2 | 73.8 | 72.8 | 63.2 | 37.5 | 43.0 | 83.2 | 88.2 | 81.8 | 86.0 | 67.3 | 5 |
| Qwen-14B-Chat | 61.0 | 53.0 | 77.4 | 74.5 | 71.0 | 39.4 | 45.7 | 82.4 | 81.4 | 81.2 | 72.4 | 65.2 | 6 |
| GLM4-9B-Chat | 56.6 | 50.2 | 76.7 | 66.6 | 58.9 | 32.2 | 53.1 | 72.0 | 84.0 | 79.8 | 82.8 | 62.9 | 7 |
| Yi-34B | 52.8 | 47.8 | 66.8 | 62.7 | 63.3 | 34.5 | 41.2 | 77.6 | 81.0 | 80.6 | 81.2 | 61.7 | 8 |
| Qwen-7B | 38.4 | 40.9 | 62.2 | 56.3 | 62.6 | 40.7 | 29.8 | 67.6 | 69.4 | 75.4 | 67.0 | 53.7 | 9 |
| EduChat-sft-002-13b | 30.2 | 37.2 | 51.5 | 50.2 | 57.2 | 43.1 | 40.3 | 73.4 | 75.2 | 74.2 | 71.4 | 53.2 | 10 |
| Yi-6B | 39.5 | 42.2 | 51.4 | 46.3 | 66.7 | 39.5 | 56.5 | 73.6 | 78.6 | 83.4 | 81.2 | 52.3 | 11 |
| Baichuan-13b | 32.5 | 36.7 | 40.2 | 31.3 | 56.9 | 31.6 | 36.4 | 68.3 | 60.0 | 67.6 | 58.6 | 43.5 | 12 |
| LLaMA3-8B | 37.7 | 35.2 | 40.4 | 38.2 | 52.8 | 20.6 | 36.4 | 63.2 | 70.2 | 76.6 | 58.6 | 43.5 | 13 |
| LLaMA2-Chinese-13B | 27.4 | 21.2 | 26.2 | 28.7 | 52.2 | 34.8 | 28.6 | 47.2 | 48.8 | 55.2 | 51.4 | 36.8 | 14 |

*\* Creativity tasks (5-1, 5-2, 5-3) use GPT-based evaluation*  
*All other tasks are evaluated using accuracy*

### Key Findings

Our comprehensive evaluation of both zero-shot and few-shot performance revealed several important insights:

1. **Memory vs. Application Gap**: Models demonstrate significantly stronger capabilities in Memory tasks compared to Application tasks, revealing a fundamental challenge in translating recalled knowledge into practical problem-solving scenarios. This gap persists across both zero-shot and few-shot settings.

2. **Few-shot Learning Benefits**: Most models show improved performance with few-shot examples, particularly in structured tasks. However, the improvement varies significantly across models and dimensions, with some models like Spark-X1 maintaining consistent top performance in both settings.

3. **Reasoning Challenges**: Even the highest-performing systems show a sharp decline when confronted with multi-step reasoning problems requiring sustained logical chains. Interestingly, few-shot examples provide limited improvement in reasoning tasks, indicating the need for enhanced reasoning architectures.

4. **Creativity Performance Variation**: Creativity tasks show the most dramatic variation between zero-shot and few-shot performance, with some models experiencing significant drops in few-shot settings, particularly in structured creative tasks (5-2), suggesting that examples may constrain creative output.

5. **Model Consistency**: Spark-X1 maintains the top ranking across both zero-shot (81.1%) and few-shot (77.4%) settings, demonstrating robust performance consistency. However, the performance gap between top-tier and mid-tier models narrows in few-shot settings.

6. **Ethics Stability**: Ethics represents the most stable dimension across both evaluation settings, with relatively strong performance even from mid-tier systems, though handling complex ethical scenarios involving competing values remains challenging.

7. **Instruction Tuning Advantages**: Chat-optimized variants demonstrate clear advantages in discourse understanding and content generation in both settings, indicating that supervised fine-tuning enhances instruction-following abilities consistently.

8. **Task-Specific Patterns**: Application tasks (particularly 3-1) remain challenging across all models and settings, while Memory tasks show the most consistent high performance, suggesting fundamental differences in how models process different cognitive demands.

These findings highlight the need for curriculum-balanced pretraining, improved reasoning architectures, and careful consideration of few-shot example selection to bridge the gap between knowledge retrieval and practical application in educational AI systems.

## Usage

### Running Evaluation Tasks

```bash
python -m EngEdueval.code.main \
  --task_path Edata/Memory/Primary_Formula_Recall.jsonl \
  --model_path /path/to/model \
  --model_name "Model Name" \
  --device 0 \
  --model_type qwen  # Options: qwen, glm, baichuan, llama
```

### Command-Line Options

- `--task_path`: Path to the task JSONL file
- `--model_path`: Path to the model weights or HuggingFace model ID
- `--model_name`: Name for logging and output files
- `--device`: GPU device ID (e.g., "0" or "0,1,2,3")
- `--model_type`: Type of model (qwen, glm, baichuan, or llama)
- `--is_few_shot`: Use few-shot examples (optional)
- `--few_shot_path`: Path to few-shot examples file (optional)
- `--is_vllm`: Use vLLM for faster inference (optional)
- `--tensor_parallel_size`: Number of GPUs for tensor parallelism (vLLM only)
- `--output_file`: Custom output file path (optional)

### Using vLLM for Acceleration

For faster inference on large models, you can enable vLLM:

```bash
python -m EngEdueval.code.main \
  --task_path Edata/Memory/Primary_Formula_Recall.jsonl \
  --model_path /path/to/model \
  --model_name "Model Name" \
  --device 0 \
  --model_type llama \
  --is_vllm \
  --tensor_parallel_size 4
```

## File Formats

### Task Files

Task files are in JSONL format with the following structure:

```json
{
  "subject": "mathematics",
  "ques_content": "What is 2+2?",
  "options": ["3", "4", "5", "6"],
  "ques_answer": "B",
  "ques_analyze": "The sum of 2 and 2 is 4, which corresponds to option B."
}
```

### Output Files

Model outputs are saved in JSONL format with:

```json
{
  "id": 42,
  "task_type": "multiple_choice",
  "question": "What is 2+2?",
  "reference_answer": "B",
  "model_output": "The answer is 4, so the correct option is B.",
  "processed_output": "B",
  "model_name": "Model Name",
  "timestamp": "2023-09-15 14:30:00"
}
```

## Contributing

Contributions are welcome! You can extend the framework by:

1. Adding support for new model architectures
2. Creating new task types
3. Implementing additional evaluation metrics
4. Improving prompt templates

