# prompt-engineering-cookbook
A structured collection of prompt engineering templates, techniques and patterns.

## Introduction

Working with *large language models (LLMs)* can be diverse, unpredictable, and even inaccurate if we don’t know how to use them properly. Based on the need for more precise, correct, predictable, and controllable answers, a new discipline has emerged for developers and for optimizing prompts — **prompt engineering**.

Prompt engineering helps us understand how LLMs behave, how they interpret instructions, and how to shape inputs so that the model produces the exact type of output we need. It gives developers control over the model’s “reasoning,” structure, and style of response.

The core idea is simple:
**well-designed input → high-quality output.**

In practice, this involves techniques such as:
-isolating content with delimiters,
-structuring output into HTML or JSON,
-enforcing specific rules or constraints,
-guiding the model through examples (few-shot prompting),
-refining responses iteratively,
-transforming, summarizing, or expanding text,
-shaping tone or style,
-or applying reasoning patterns like chain-of-thought or multi-step reasoning.

This Prompt Engineering Cookbook brings together the most practical techniques used by professionals — and by me — to achieve predictable and high-quality results when working with LLMs.

## Delimiters

Delimiters are boundary markers that isolate specific parts of the input so the model can clearly distinguish between instructions, context, and data.  
They improve clarity, control, reduce errors, prevent hallucinations, and increase formatting accuracy.

### **Use delimiters when:**
- the input text is long, messy, or unstructured  
- you want to separate the instruction from the data being processed  
- you are performing tasks such as summarizing, transforming, rewriting, or extracting  
- you need structured or predictable output  
- you want to avoid the model “mixing” context with commands  

---

## **Types of Delimiters and Examples**

### **1. Triple backticks** \`\`\`
Used for:
- code of any type (Python, Java, HTML, etc.)
- isolating raw text blocks

**Example:**
\`\`\`
def add(a,b)
    return a+b
\`\`\`

---

### **2. Triple quotes** `""" ... """`
Used for:
- long text passages
- essays, articles, paragraphs

**Example:**
Summarize the following text:
"""
Delimiters are boundary markers that help structure input for LLMs...
"""

---

### **3. Triple dashes** `---`
Used for:
- separating sections
- multi-part input

**Example:**

--- Introduction ---
{TEXT}

--- Article ---
{TEXT}

---

### **4. Angle brackets** `< >`
Used for:
- variables or user inputs  
- short placeholders

**Example:**
Hello `<name>`
Your message is: `<TEXT>`

---

### **5. XML-style tags** `<tag> </tag>`
Used for:
- strict structured formatting  
- avoiding ambiguity in multi-section prompts  
- machine-readable output

**Example:**
`<input>`
{TEXT}  
`</input>`


## Structured Outputs (HTML, JSON)

## Verifying Conditions

## Few-Shot Prompting

## Iterative Prompting

## Summarizing

## Inferring

## Transforming

## Expanding

## Chain-of-Thought Reasoning

## Chaining Prompts

## Appendix