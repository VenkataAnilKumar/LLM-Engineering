# 🏆 Benchmarks & Evaluation

Comprehensive benchmarks, evaluation datasets, leaderboards, and testing frameworks.

## 📊 Legend

- 🟢 **Easy** - Simple to run locally
- 🟡 **Moderate** - Requires some setup
- 🔴 **Complex** - Specialized infrastructure needed
- 🎯 **Category** - Benchmark focus area
- 📏 **Metrics** - Evaluation criteria
- 📅 **Updated** - Last verified date

---

## 📑 Table of Contents

1. [🧠 General Knowledge](#-general-knowledge)
2. [💻 Code Generation](#-code-generation)
3. [🧮 Math & Reasoning](#-math--reasoning)
4. [📖 Reading Comprehension](#-reading-comprehension)
5. [🌍 Multilingual](#-multilingual)
6. [⚖️ Safety & Bias](#️-safety--bias)
7. [🔍 Factuality & Hallucination](#-factuality--hallucination)
8. [🤖 Agent Benchmarks](#-agent-benchmarks)
9. [🏅 Leaderboards](#-leaderboards)
10. [🛠️ Evaluation Frameworks](#️-evaluation-frameworks)
11. [🔀 Benchmark Comparison](#-benchmark-comparison)

---

## 🧠 General Knowledge

### MMLU (Massive Multitask Language Understanding)
- 🟢 Easy | 🎯 General Knowledge | 📏 Accuracy | 📅 Oct 2025
- **URL:** https://github.com/hendrycks/test
- **Paper:** https://arxiv.org/abs/2009.03300
- **Size:** 15,908 questions across 57 subjects
- **Topics:** STEM, humanities, social sciences, professional fields
- **Note:** Gold standard for measuring general knowledge and reasoning.

### HellaSwag
- 🟢 Easy | 🎯 Commonsense Reasoning | 📏 Accuracy | 📅 Oct 2025
- **URL:** https://rowanzellers.com/hellaswag/
- **Paper:** https://arxiv.org/abs/1905.07830
- **Size:** 70,000 questions
- **Note:** Tests commonsense reasoning about physical situations.

### Winogrande
- 🟢 Easy | 🎯 Commonsense Reasoning | 📏 Accuracy | 📅 Oct 2025
- **URL:** https://winogrande.allenai.org/
- **Paper:** https://arxiv.org/abs/1907.10641
- **Size:** 44,000 problems
- **Note:** Tests pronoun resolution requiring commonsense reasoning.

### ARC (AI2 Reasoning Challenge)
- 🟢 Easy | 🎯 Science Reasoning | 📏 Accuracy | 📅 Oct 2025
- **URL:** https://allenai.org/data/arc
- **Paper:** https://arxiv.org/abs/1803.05457
- **Size:** 7,787 science questions
- **Difficulty:** Easy and Challenge sets
- **Note:** Grade-school science questions requiring reasoning.

### TruthfulQA
- 🟡 Moderate | 🎯 Truthfulness | 📏 % True & Informative | 📅 Oct 2025
- **URL:** https://github.com/sylinrl/TruthfulQA
- **Paper:** https://arxiv.org/abs/2109.07958
- **Size:** 817 questions
- **Note:** Tests model's truthfulness and tendency to reproduce common falsehoods.

---

## 💻 Code Generation

### HumanEval
- 🟢 Easy | 🎯 Python Code | 📏 Pass@k | 📅 Oct 2025
- **URL:** https://github.com/openai/human-eval
- **Paper:** https://arxiv.org/abs/2107.03374
- **Size:** 164 programming problems
- **Language:** Python
- **Metric:** Pass@1, Pass@10, Pass@100
- **Note:** Hand-written programming problems from OpenAI.

### MBPP (Mostly Basic Python Problems)
- 🟢 Easy | 🎯 Python Code | 📏 Pass@k | 📅 Oct 2025
- **URL:** https://github.com/google-research/google-research/tree/master/mbpp
- **Paper:** https://arxiv.org/abs/2108.07732
- **Size:** 974 programming problems
- **Language:** Python
- **Note:** Entry-level Python programming tasks with test cases.

### MultiPL-E
- 🟡 Moderate | 🎯 Multi-language Code | 📏 Pass@k | 📅 Oct 2025
- **URL:** https://github.com/nuprl/MultiPL-E
- **Paper:** https://arxiv.org/abs/2208.08227
- **Languages:** 18+ including Python, Java, C++, JavaScript, Rust
- **Note:** HumanEval translated to multiple programming languages.

### CodeXGLUE
- 🟡 Moderate | 🎯 Code Understanding | 📏 Various | 📅 Oct 2025
- **URL:** https://github.com/microsoft/CodeXGLUE
- **Paper:** https://arxiv.org/abs/2102.04664
- **Tasks:** 14 tasks including code search, completion, translation
- **Note:** Comprehensive benchmark for code intelligence.

### DS-1000
- 🟡 Moderate | 🎯 Data Science Code | 📏 Pass@k | 📅 Oct 2025
- **URL:** https://github.com/xlang-ai/DS-1000
- **Paper:** https://arxiv.org/abs/2211.11501
- **Size:** 1,000 data science problems
- **Libraries:** NumPy, Pandas, PyTorch, TensorFlow, etc.
- **Note:** Real-world data science coding tasks.

---

## 🧮 Math & Reasoning

### GSM8K (Grade School Math)
- 🟢 Easy | 🎯 Math Word Problems | 📏 Accuracy | 📅 Oct 2025
- **URL:** https://github.com/openai/grade-school-math
- **Paper:** https://arxiv.org/abs/2110.14168
- **Size:** 8,500 grade school math problems
- **Note:** Multi-step mathematical reasoning with natural language solutions.

### MATH
- 🟡 Moderate | 🎯 Competition Math | 📏 Accuracy | 📅 Oct 2025
- **URL:** https://github.com/hendrycks/math
- **Paper:** https://arxiv.org/abs/2103.03874
- **Size:** 12,500 competition math problems
- **Difficulty:** High school competition level
- **Note:** Challenging mathematical reasoning problems.

### MathQA
- 🟢 Easy | 🎯 Math Reasoning | 📏 Accuracy | 📅 Oct 2025
- **URL:** https://math-qa.github.io/
- **Paper:** https://arxiv.org/abs/1905.13319
- **Size:** 37,000 math word problems
- **Note:** Multiple-choice math questions with detailed solutions.

### TheoremQA
- 🟡 Moderate | 🎯 STEM Reasoning | 📏 Accuracy | 📅 Oct 2025
- **URL:** https://github.com/wenhuchen/TheoremQA
- **Paper:** https://arxiv.org/abs/2305.12524
- **Size:** 800+ STEM problems
- **Topics:** Math, physics, EE, CS
- **Note:** Tests theorem application in STEM domains.

---

## 📖 Reading Comprehension

### SQuAD 2.0
- 🟢 Easy | 🎯 Reading Comprehension | 📏 F1, EM | 📅 Oct 2025
- **URL:** https://rajpurkar.github.io/SQuAD-explorer/
- **Paper:** https://arxiv.org/abs/1806.03822
- **Size:** 150,000+ questions
- **Note:** Reading comprehension with unanswerable questions.

### RACE
- 🟢 Easy | 🎯 Reading Comprehension | 📏 Accuracy | 📅 Oct 2025
- **URL:** https://www.cs.cmu.edu/~glai1/data/race/
- **Paper:** https://arxiv.org/abs/1704.04683
- **Size:** 28,000+ passages, 100,000+ questions
- **Source:** Chinese English exams
- **Note:** Challenging reading comprehension from educational materials.

### BoolQ
- 🟢 Easy | 🎯 Yes/No Questions | 📏 Accuracy | 📅 Oct 2025
- **URL:** https://github.com/google-research-datasets/boolean-questions
- **Paper:** https://arxiv.org/abs/1905.10044
- **Size:** 15,942 yes/no questions
- **Note:** Naturally occurring yes/no questions from Google search.

---

## 🌍 Multilingual

### XNLI (Cross-lingual NLI)
- 🟡 Moderate | 🎯 Multilingual NLI | 📏 Accuracy | 📅 Oct 2025
- **URL:** https://github.com/facebookresearch/XNLI
- **Paper:** https://arxiv.org/abs/1809.05053
- **Languages:** 15 languages
- **Note:** Natural language inference across languages.

### MLQA (Multilingual QA)
- 🟡 Moderate | 🎯 Multilingual QA | 📏 F1, EM | 📅 Oct 2025
- **URL:** https://github.com/facebookresearch/MLQA
- **Paper:** https://arxiv.org/abs/1910.07475
- **Languages:** 7 languages
- **Note:** Cross-lingual question answering.

### FLORES
- 🟡 Moderate | 🎯 Machine Translation | 📏 BLEU, chrF++ | 📅 Oct 2025
- **URL:** https://github.com/facebookresearch/flores
- **Paper:** https://arxiv.org/abs/2106.03193
- **Languages:** 200+ languages
- **Note:** Low-resource translation evaluation.

---

## ⚖️ Safety & Bias

### BBQ (Bias Benchmark for QA)
- 🟡 Moderate | 🎯 Bias Detection | 📏 Accuracy, Bias Score | 📅 Oct 2025
- **URL:** https://github.com/nyu-mll/BBQ
- **Paper:** https://arxiv.org/abs/2110.08193
- **Size:** 58,000 questions
- **Categories:** Age, disability, gender, race, religion, etc.
- **Note:** Tests social biases in question answering.

### BOLD (Bias in Open-ended Language Generation)
- 🟡 Moderate | 🎯 Generation Bias | 📏 Various sentiment metrics | 📅 Oct 2025
- **URL:** https://github.com/amazon-science/bold
- **Paper:** https://arxiv.org/abs/2101.11718
- **Note:** Measures biases in open-ended text generation.

### RealToxicityPrompts
- 🟡 Moderate | 🎯 Toxicity | 📏 Toxicity Score | 📅 Oct 2025
- **URL:** https://github.com/allenai/real-toxicity-prompts
- **Paper:** https://arxiv.org/abs/2009.11462
- **Size:** 100,000 prompts
- **Note:** Tests model tendency to generate toxic content.

### AdvGLUE
- 🟡 Moderate | 🎯 Adversarial Robustness | 📏 Accuracy | 📅 Oct 2025
- **URL:** https://adversarialglue.github.io/
- **Paper:** https://arxiv.org/abs/2111.02840
- **Note:** Adversarial examples for GLUE tasks.

---

## 🔍 Factuality & Hallucination

### FEVER (Fact Extraction and VERification)
- 🟡 Moderate | 🎯 Fact Verification | 📏 Label Accuracy, FEVER Score | 📅 Oct 2025
- **URL:** https://fever.ai/
- **Paper:** https://arxiv.org/abs/1803.05355
- **Size:** 185,000 claims
- **Note:** Verifying claims against Wikipedia.

### HaluEval
- 🟡 Moderate | 🎯 Hallucination Detection | 📏 Detection Rate | 📅 Oct 2025
- **URL:** https://github.com/RUCAIBox/HaluEval
- **Paper:** https://arxiv.org/abs/2305.11747
- **Size:** 35,000 samples
- **Note:** Detecting LLM hallucinations across tasks.

### SelfCheckGPT
- 🟡 Moderate | 🎯 Hallucination Detection | 📏 Various metrics | 📅 Oct 2025
- **URL:** https://github.com/potsawee/selfcheckgpt
- **Paper:** https://arxiv.org/abs/2303.08896
- **Note:** Zero-resource hallucination detection.

---

## 🤖 Agent Benchmarks

### WebArena
- 🔴 Complex | 🎯 Web Agents | 📏 Task Success Rate | 📅 Oct 2025
- **URL:** https://github.com/web-arena-x/webarena
- **Paper:** https://arxiv.org/abs/2307.13854
- **Size:** 812 web-based tasks
- **Note:** Realistic web environment for autonomous agents.

### AgentBench
- 🔴 Complex | 🎯 Agent Capabilities | 📏 Success Rate | 📅 Oct 2025
- **URL:** https://github.com/THUDM/AgentBench
- **Paper:** https://arxiv.org/abs/2308.03688
- **Environments:** 8 diverse environments
- **Note:** Multi-dimensional agent evaluation.

### GAIA (General AI Assistants)
- 🔴 Complex | 🎯 General Assistant | 📏 Task Completion | 📅 Oct 2025
- **URL:** https://huggingface.co/gaia-benchmark
- **Paper:** https://arxiv.org/abs/2311.12983
- **Size:** 466 real-world questions
- **Note:** Tests general assistant capabilities with tools.

### ToolBench
- 🟡 Moderate | 🎯 Tool Use | 📏 Pass Rate | 📅 Oct 2025
- **URL:** https://github.com/OpenBMB/ToolBench
- **Paper:** https://arxiv.org/abs/2305.16504
- **Tools:** 16,000+ real-world APIs
- **Note:** Tool manipulation and reasoning.

---

## 🏅 Leaderboards

### Open LLM Leaderboard (Hugging Face)
- **URL:** https://huggingface.co/spaces/HuggingFaceH4/open_llm_leaderboard
- **Benchmarks:** MMLU, ARC, HellaSwag, TruthfulQA, Winogrande, GSM8K
- **Note:** Most comprehensive open model leaderboard.

### ChatBot Arena (LMSYS)
- **URL:** https://chat.lmsys.org/?leaderboard
- **Method:** Human preference evaluation (Elo ratings)
- **Note:** Crowdsourced head-to-head model comparisons.

### AlpacaEval
- **URL:** https://github.com/tatsu-lab/alpaca_eval
- **Method:** Automated evaluation using GPT-4 as judge
- **Note:** Fast, cheap evaluation of instruction-following models.

### MT-Bench
- **URL:** https://github.com/lm-sys/FastChat/tree/main/fastchat/llm_judge
- **Method:** Multi-turn conversation evaluation
- **Note:** 80 high-quality multi-turn questions.

### Big Code Models Leaderboard
- **URL:** https://huggingface.co/spaces/bigcode/bigcode-models-leaderboard
- **Benchmarks:** HumanEval, MBPP, MultiPL-E
- **Note:** Code generation model rankings.

---

## 🛠️ Evaluation Frameworks

### lm-evaluation-harness
- 🟢 Easy | ⏱️ 1 hour setup | 📅 Oct 2025
- **URL:** https://github.com/EleutherAI/lm-evaluation-harness
- **License:** MIT
- **Benchmarks:** 200+ tasks
- **Note:** Unified framework for LLM evaluation.

### OpenAI Evals
- 🟢 Easy | ⏱️ 30 min setup | 📅 Oct 2025
- **URL:** https://github.com/openai/evals
- **License:** MIT
- **Note:** Framework for evaluating OpenAI models and custom evals.

### DeepEval
- 🟢 Easy | ⏱️ 30 min setup | 📅 Oct 2025
- **URL:** https://github.com/confident-ai/deepeval
- **License:** Apache 2.0
- **Note:** Unit testing framework for LLMs with CI/CD integration.

### promptfoo
- 🟢 Easy | ⏱️ 15 min setup | 📅 Oct 2025
- **URL:** https://github.com/promptfoo/promptfoo
- **License:** MIT
- **Note:** Test and evaluate prompts systematically.

### HELM (Holistic Evaluation of Language Models)
- 🟡 Moderate | ⏱️ 2 hours setup | 📅 Oct 2025
- **URL:** https://crfm.stanford.edu/helm/
- **Scenarios:** 42 scenarios, 59 metrics
- **Note:** Comprehensive evaluation across multiple dimensions.

---

## 🔀 Benchmark Comparison

### General Knowledge Benchmarks

| Benchmark | Difficulty | Size | Focus | Best Models (Oct 2025) |
|-----------|------------|------|-------|------------------------|
| **MMLU** | 🔴 Hard | 15.9K | Broad knowledge | GPT-4: 86%, Claude 3: 85% |
| **HellaSwag** | 🟡 Medium | 70K | Commonsense | GPT-4: 95%, Mixtral: 87% |
| **ARC-Challenge** | 🟡 Medium | 3K | Science reasoning | GPT-4: 96%, LLaMA 2 70B: 85% |
| **TruthfulQA** | 🔴 Hard | 817 | Truthfulness | GPT-4: 59%, Claude 3: 55% |
| **Winogrande** | 🟡 Medium | 44K | Pronoun resolution | GPT-4: 87%, Mixtral: 85% |

### Code Benchmarks

| Benchmark | Language(s) | Difficulty | Size | Pass@1 Leaders |
|-----------|-------------|------------|------|----------------|
| **HumanEval** | Python | 🟡 Medium | 164 | GPT-4: 67%, Claude 3: 65% |
| **MBPP** | Python | 🟢 Easy | 974 | GPT-4: 75%, StarCoder: 52% |
| **MultiPL-E** | 18+ languages | 🟡 Medium | ~3K | GPT-4: varies by lang |
| **DS-1000** | Python (DS) | 🔴 Hard | 1K | GPT-4: 52%, specialized models |

### Math Benchmarks

| Benchmark | Difficulty | Size | Type | Accuracy Leaders |
|-----------|------------|------|------|------------------|
| **GSM8K** | 🟡 Medium | 8.5K | Grade school | GPT-4: 92%, Gemini Pro: 87% |
| **MATH** | 🔴 Hard | 12.5K | Competition | GPT-4: 52%, Minerva: 50% |
| **MathQA** | 🟡 Medium | 37K | Word problems | GPT-4: 85%, PaLM 2: 82% |

### Evaluation Framework Comparison

| Framework | Ease of Use | Benchmarks | Custom Evals | Integration |
|-----------|-------------|------------|--------------|-------------|
| **lm-evaluation-harness** | 🟢 Easy | 200+ | ✅ Yes | CLI, Python |
| **OpenAI Evals** | 🟢 Easy | Many | ✅ Easy | OpenAI API |
| **DeepEval** | 🟢 Very Easy | Built-in | ✅ Yes | Pytest, CI/CD |
| **promptfoo** | 🟢 Very Easy | Custom | ✅ Yes | CLI, CI/CD |
| **HELM** | 🟡 Moderate | 42 scenarios | 🟡 Complex | Research-focused |

---

## 🎓 Evaluation Best Practices

### Choosing Benchmarks

**For General-Purpose Models:**
- Must: MMLU, HellaSwag, ARC, TruthfulQA, GSM8K
- Optional: Winogrande, BBQ, RACE

**For Code Models:**
- Must: HumanEval, MBPP
- Optional: MultiPL-E (for multi-language), DS-1000 (for data science)

**For Chat/Assistant Models:**
- Must: MT-Bench, AlpacaEval
- Optional: ChatBot Arena (human eval)

**For Safety/Alignment:**
- Must: TruthfulQA, BBQ
- Optional: RealToxicityPrompts, BOLD

### Running Evaluations

**Step 1: Choose Framework**
- Start with `lm-evaluation-harness` for academic benchmarks
- Use `DeepEval` for production application testing
- Use `promptfoo` for prompt optimization

**Step 2: Run Standard Benchmarks**
```bash
# Example with lm-evaluation-harness
lm_eval --model hf --model_args pretrained=mistralai/Mistral-7B-v0.1 \
  --tasks mmlu,hellaswag,arc_challenge,gsm8k --batch_size 8
```

**Step 3: Custom Evaluation**
- Create domain-specific test sets
- Use GPT-4 as judge for open-ended tasks
- Collect human feedback for critical applications

**Step 4: Track Over Time**
- Version control eval results
- Track across model iterations
- Monitor for regression

### Interpreting Results

**What Good Scores Mean:**
- **MMLU > 70%**: Strong general knowledge
- **HumanEval > 50%**: Good code generation
- **GSM8K > 80%**: Strong math reasoning
- **TruthfulQA > 50%**: Better than average truthfulness

**Red Flags:**
- Big gap between benchmarks (overfit to specific tests)
- Poor TruthfulQA despite good MMLU (knowledge without truthfulness)
- High variance across runs (unstable model)
- Perfect scores on old benchmarks (training data contamination)

### Avoiding Common Pitfalls

❌ **Don't:**
- Rely on single benchmark
- Ignore data contamination
- Compare across different evaluation settings
- Treat benchmarks as the only quality measure

✅ **Do:**
- Use multiple diverse benchmarks
- Test on unseen/new benchmarks
- Include human evaluation for production
- Benchmark your specific use case
- Track confidence intervals/variance

---

**Last Updated:** October 2025
