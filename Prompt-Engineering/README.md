# 🎨 Prompt Engineering

Master the art and science of crafting effective prompts to get the best results from Large Language Models.

---

## 🎯 Table of Contents

1. [Introduction](#introduction)
2. [Basic Techniques](#basic-techniques)
3. [Advanced Techniques](#advanced-techniques)
4. [Prompt Templates](#prompt-templates)
5. [Domain-Specific Prompting](#domain-specific-prompting)
6. [Best Practices](#best-practices)
7. [Common Pitfalls](#common-pitfalls)
8. [Resources](#resources)

---

## 📖 Introduction

### What is Prompt Engineering?

The practice of designing and refining inputs (prompts) to elicit desired outputs from language models. It's the primary way to control and guide LLM behavior without modifying the model itself.

### Why It Matters

- ✅ No training required
- ✅ Immediate results
- ✅ Cost-effective
- ✅ Highly flexible
- ✅ Rapidly iterate

---

## 🎓 Basic Techniques

### 1. Clear Instructions

**Principle**: Be explicit about what you want

**Bad**:
```
Write about AI
```

**Good**:
```
Write a 300-word explanation of artificial intelligence 
for a 10-year-old, using simple language and everyday examples.
```

**Key Elements**:
- Specific task
- Length/format
- Audience
- Tone/style
- Constraints

---

### 2. Few-Shot Learning

**Principle**: Provide examples

**Format**:
```
Example 1:
Input: "I love this product!"
Output: Positive

Example 2:
Input: "Terrible experience, never again."
Output: Negative

Example 3:
Input: "It's okay, nothing special."
Output: Neutral

Now classify this:
Input: "Amazing quality, highly recommend!"
Output:
```

**Benefits**:
- Model learns pattern
- Consistent format
- Better accuracy

**Tips**:
- Use 2-5 examples
- Diverse examples
- Representative of task

---

### 3. Zero-Shot Prompting

**Principle**: Clear instructions without examples

**Example**:
```
Classify the sentiment of the following review as 
Positive, Negative, or Neutral:

Review: "The product exceeded my expectations!"
Sentiment:
```

**When to Use**:
- Simple tasks
- Limited examples available
- Testing model capabilities

---

### 4. Role Assignment

**Principle**: Give the model a persona

**Template**:
```
You are [role with expertise].
[Task description]
[Additional constraints]
```

**Examples**:
```
You are an expert Python developer with 10 years of experience.
Review the following code and suggest improvements for
readability and performance.
```

```
You are a patient teacher explaining concepts to beginners.
Explain quantum computing in simple terms.
```

---

### 5. Step-by-Step Instructions

**Principle**: Break down complex tasks

**Template**:
```
Follow these steps:
1. [First step]
2. [Second step]
3. [Third step]
...

Input: [data]
Output:
```

**Example**:
```
Analyze this sentence step by step:
1. Identify the subject and predicate
2. List all nouns and verbs
3. Determine the sentence type
4. Assess grammatical correctness

Sentence: "The quick brown fox jumps over the lazy dog."
```

---

## 🚀 Advanced Techniques

### 1. Chain-of-Thought (CoT)

**Principle**: Encourage reasoning steps

**Basic CoT**:
```
Question: Roger has 5 tennis balls. He buys 2 more cans of 
tennis balls. Each can has 3 balls. How many tennis balls 
does he have now?

Answer: Let's think step by step.
```

**Result**:
```
Roger started with 5 balls.
2 cans × 3 balls per can = 6 balls
5 + 6 = 11 balls total
Answer: 11
```

**When to Use**:
- Math problems
- Logical reasoning
- Multi-step tasks
- Complex analysis

---

### 2. Self-Consistency

**Principle**: Generate multiple reasoning paths, use majority vote

**Process**:
1. Generate 5-10 answers
2. Each with different reasoning
3. Take most common answer

**Implementation**:
```
Use temperature > 0 for diversity
Run same prompt multiple times
Aggregate results
```

**Benefit**: Improved accuracy on reasoning tasks

---

### 3. Tree of Thoughts (ToT)

**Principle**: Explore multiple solution paths

**Structure**:
```
Problem: [complex problem]

Approach 1:
- Step 1a
- Step 1b
- Evaluation: [score]

Approach 2:
- Step 2a
- Step 2b
- Evaluation: [score]

Best approach: [selected]
Final solution: [complete]
```

**Use Cases**:
- Creative problem solving
- Strategic planning
- Multiple valid solutions

---

### 4. ReAct (Reasoning + Acting)

**Principle**: Combine thinking and acting

**Format**:
```
Thought: [reasoning]
Action: [tool use]
Observation: [result]
Thought: [next reasoning]
Action: [next action]
...
Answer: [final answer]
```

**Example**:
```
Question: What's the capital of the country where the Eiffel Tower is located?

Thought: I need to find where the Eiffel Tower is located first.
Action: Search[Eiffel Tower location]
Observation: The Eiffel Tower is in Paris, France.
Thought: Now I know it's in France. I need the capital of France.
Action: Search[Capital of France]
Observation: The capital of France is Paris.
Thought: I now have the answer.
Answer: Paris
```

---

### 5. Generated Knowledge

**Principle**: First generate relevant knowledge, then answer

**Two-Step Process**:

**Step 1 - Generate Knowledge**:
```
Generate relevant facts about quantum computing.
```

**Step 2 - Use Knowledge**:
```
Based on the following facts about quantum computing:
[generated knowledge]

Explain quantum supremacy in simple terms.
```

---

### 6. Least-to-Most Prompting

**Principle**: Break problems into sub-problems

**Template**:
```
Problem: [complex problem]

Let's break this down:
1. What is the simplest part?
2. Solve the simplest part
3. What's the next part?
4. Solve using previous answer
...

Final answer: [combined solution]
```

---

### 7. Constrained Generation

**Principle**: Control output format

**Examples**:

**JSON Output**:
```
Extract information and return as JSON:

Text: "John Smith works at Google as a Software Engineer."

Format:
{
  "name": "",
  "company": "",
  "role": ""
}
```

**Bullet Points**:
```
List 5 benefits of exercise.
Return as bullet points starting with "•"
```

**Word Limit**:
```
Explain machine learning in exactly 50 words.
```

---

## 📋 Prompt Templates

### Classification

```
Classify the following [item] into one of these categories:
[Category 1], [Category 2], [Category 3]

[Item]: [text]

Category:
```

---

### Summarization

```
Summarize the following text in [X] sentences.
Focus on [key aspects].

Text: [input text]

Summary:
```

---

### Information Extraction

```
Extract the following information from the text:
- [Field 1]
- [Field 2]
- [Field 3]

Text: [input]

Extracted Information:
```

---

### Question Answering

```
Answer the question based on the context below.
If the answer is not in the context, say "I don't know."

Context: [text]

Question: [question]

Answer:
```

---

### Creative Writing

```
Write a [type] about [topic] in the style of [style].

Requirements:
- Length: [X words/sentences]
- Tone: [tone]
- Include: [elements]

[Type]:
```

---

### Code Generation

```
Write a [language] function that:
- [Requirement 1]
- [Requirement 2]
- [Requirement 3]

Include:
- Function name: [name]
- Parameters: [params]
- Return type: [type]
- Comments explaining the logic

Code:
```

---

## 🎯 Domain-Specific Prompting

### Technical Documentation

```
Create technical documentation for [feature/API]:

Include:
1. Overview
2. Prerequisites
3. Step-by-step instructions
4. Code examples
5. Common issues and solutions

Target audience: [level]
```

---

### Data Analysis

```
Analyze the following data and provide:
1. Key insights
2. Trends or patterns
3. Anomalies
4. Recommendations

Data: [data]

Analysis:
```

---

### Customer Support

```
You are a customer support agent for [company].

Customer issue: [description]

Provide:
1. Empathetic acknowledgment
2. Clear explanation
3. Step-by-step solution
4. Follow-up questions if needed

Response:
```

---

### Content Creation

```
Create [content type] for [platform] about [topic]:

Requirements:
- Target audience: [audience]
- Tone: [tone]
- Length: [length]
- Call-to-action: [CTA]
- Keywords: [keywords]

Content:
```

---

## ✅ Best Practices

### Structure

1. **Be Specific**: Vague prompts = vague outputs
2. **Provide Context**: Background helps the model
3. **Use Delimiters**: Separate sections clearly (```, ---, ###)
4. **Specify Format**: JSON, list, paragraph, etc.
5. **Set Constraints**: Length, style, content boundaries

### Iteration

1. **Start Simple**: Basic prompt first
2. **Test and Refine**: Iterate based on outputs
3. **Add Examples**: If zero-shot doesn't work
4. **Use Reasoning**: Add "think step by step" for complex tasks
5. **Version Control**: Save successful prompts

### Clarity

1. **Active Voice**: "List the items" vs "Items should be listed"
2. **Positive Instructions**: Say what to do, not what not to do
3. **One Task at a Time**: Don't cram too much
4. **Explicit Constraints**: Be clear about boundaries

---

## ⚠️ Common Pitfalls

### 1. Ambiguity

**Bad**:
```
Tell me about Python
```
(Python the language or the snake?)

**Good**:
```
Explain the key features of Python programming language
```

---

### 2. Assuming Knowledge

**Bad**:
```
Use the Smith-Jones algorithm
```

**Good**:
```
Use the Smith-Jones algorithm (a method for X that does Y)
```

---

### 3. Too Complex

**Bad**:
```
Analyze the sentiment, extract entities, summarize, 
translate to Spanish, and rate quality
```

**Good**:
Break into separate prompts or explicit steps

---

### 4. Hallucination Encouragement

**Bad**:
```
Tell me everything about [obscure topic]
```

**Good**:
```
Based on the following information: [provide context]
Explain [topic]. If information is insufficient, state what's missing.
```

---

### 5. Inconsistent Formatting

**Bad**:
```
example 1: input -> output
Ex2 - input: output
```

**Good**:
```
Example 1:
Input: [text]
Output: [result]

Example 2:
Input: [text]
Output: [result]
```

---

## 🎯 Optimization Tips

### Temperature & Parameters

**Temperature**:
- 0.0-0.3: Focused, consistent (factual tasks)
- 0.7-1.0: Balanced (general use)
- 1.0-2.0: Creative, diverse (creative writing)

**Top-P**:
- 0.1: Very focused
- 0.9: Standard
- 1.0: Maximum diversity

**Max Tokens**:
- Set appropriately for expected output
- Leave buffer for reasoning

---

### Prompt Length

**Optimal**:
- Be concise but complete
- Include necessary context
- Remove redundancy

**Context Window**:
- Be aware of model limits
- Prioritize recent context
- Summarize if needed

---

## 📚 Learning Resources

### Free Courses

**[Learn Prompting](https://learnprompting.org/)** ⭐⭐⭐
- Comprehensive free course
- Interactive examples
- Regular updates

**[Prompt Engineering Guide](https://www.promptingguide.ai/)** ⭐⭐⭐
- Techniques and examples
- Research-backed
- Multilingual

**[DeepLearning.AI - ChatGPT Prompt Engineering](https://www.deeplearning.ai/short-courses/chatgpt-prompt-engineering-for-developers/)** ⭐⭐⭐
- Taught by Andrew Ng
- Practical focus
- Free

---

### Books & Papers

**Papers**:
- Chain-of-Thought: https://arxiv.org/abs/2201.11903
- ReAct: https://arxiv.org/abs/2210.03629
- Tree of Thoughts: https://arxiv.org/abs/2305.10601

**Guides**:
- OpenAI Best Practices: https://platform.openai.com/docs/guides/prompt-engineering
- Anthropic Prompt Engineering: https://docs.anthropic.com/claude/docs/prompt-engineering

---

### Tools

**[OpenAI Playground](https://platform.openai.com/playground)**
- Interactive testing
- Parameter tuning

**[PromptPerfect](https://promptperfect.jina.ai/)**
- Optimize prompts automatically

**[LangChain Hub](https://smith.langchain.com/hub)**
- Share and discover prompts

---

## 💡 Pro Tips

> **Tip 1**: Always test with multiple inputs

> **Tip 2**: Keep a prompt library of what works

> **Tip 3**: Use few-shot when zero-shot fails

> **Tip 4**: Add "Let's think step by step" for reasoning

> **Tip 5**: Specify output format explicitly

> **Tip 6**: Start with examples from documentation

> **Tip 7**: Version control your prompts like code

---

## 🔬 Advanced Resources

### Prompt Optimization

**Automatic Prompt Engineering**:
- APE: https://arxiv.org/abs/2211.01910
- OptiGuide: https://arxiv.org/abs/2307.03172

**Prompt Compression**:
- LLMLingua: https://arxiv.org/abs/2310.06201

---

### Research Papers

**Meta-Prompting**:
- Teaching models to prompt themselves

**Prompt Chaining**:
- Breaking complex tasks into chains

**Recursive Prompting**:
- Self-improvement loops

---

<div align="center">

**[⬆ Back to Top](#-prompt-engineering)**

*"The art of asking the right question."*

</div>
