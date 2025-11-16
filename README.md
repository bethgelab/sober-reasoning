# 🧠 Sober Reasoning: Evaluation Code


This repository hosts evaluation code from our paper:

**"A Sober Look at Progress in Language Model Reasoning: Pitfalls and Paths to Reproducibility"**

📄 [Paper](https://arxiv.org/abs/2504.07086)  
📊 [Leaderboard](https://bethgelab.github.io/sober-reasoning/)  
🧪 [HuggingFace Dataset Page](https://huggingface.co/datasets/bethgelab/sober_reasoning)


## 🚀 Quickstart: Running an Evaluation

To launch a single evaluation run, use:
```
python main.py \
    --model deepseek-ai/DeepSeek-R1-Distill-Qwen-1.5B \
    --task "custom|aime24|0|0" \
    --temperature 0.8 \
    --top_p 0.9 \
    --seed 0 \
    --output_dir /path/to/output \
    --max_new_tokens 32768 \
    --max_model_length 32768 \
    --custom_tasks_directory lighteval_tasks.py \
    --use_chat_template
```
Replace `--task` with the appropriate benchmark specification (e.g., `aime24`, `math_500`, etc.).

## 🧱 Infrastructure Setup
### 🔁 Runpod (Single GPU Inference)

1. Build the Docker image from the provided Dockerfile:
   ```
   docker build -t sober-reasoning-eval .
   ```

2. Launch a Runpod instance using this image.

3. SSH into the instance and run:
   ```
   python main.py ...
   ```

### 🧵 Slurm (Multi-Seed, Multi-Task, Multi-Temp Grid)

1. Set the following variables inside run.sh:
   - `LOCAL_DIR`: Path to cloned repo
   - `OUTPUT_DIR`: Path for logs and outputs
   - `PARTITION`: Your Slurm partition name
   - `VENV`: Path to your Python virtual environment

2. Configure task/seed/temp/... ranges inside `run.sh`.

3. Submit the batch job:
   ```
   bash run.sh
   ```

## 🔄 Citation

```bibtex
@inproceedings{hochlehnert2025soberreasoning,
    title={A Sober Look at Progress in Language Model Reasoning: Pitfalls and Paths to Reproducibility},
    author={Andreas Hochlehnert and Hardik Bhatnagar and Vishaal Udandarao and Samuel Albanie and Ameya Prabhu and Matthias Bethge},
    booktitle={Second Conference on Language Modeling},
    year={2025},
    url={https://openreview.net/forum?id=90UrTTxp5O}
}
```

