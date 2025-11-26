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

---

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

### **Types of Delimiters and Examples**

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

---

## Structured Outputs (HTML, JSON)

Specifying that the output format should be in a defined **JSON**, **HTML**, or **XML** structure for easier subsequent manipulation. Structured output ensures that the model returns information in a predictable, machine-readable format. This makes it easier to post-process, validate, and integrate into applications or pipelines.

---

**When to use sctructured outputs**
- you need consistent formating
- you plan to parse the output programmatically
- you need the model to follow a schema (JSON keys, HTML tags)

---

**Example**

**Instruction:**
“Extract the following information and return it in JSON format.”

**Input:**

---

## Verifying Conditions

When we need the output to be safe, accurate, or internally appropriate, we must introduce checks that verify whether the model’s response complies with the instructions. This method is known as **Verifying Conditions**. Verification can be done from two primary perspectives:
- Moderation API  
- Model-evaluates-model

---

**Moderation API**
This verifies that the output does not contain prohibited content (violence, hate, sexuality, self-harm…) and returns safety categories and risk scores.

If the content is flagged, the system can:
- display a fallback response  
- generate a new response  
- block the output entirely  

---

**Model-evaluates-model**
The second strategy is to use the model itself to check the quality of its own output.

Process:
- the model generates an answer for the user  
- the answer is sent back to the model together with the original question  
- the model responds YES/NO based on whether:  
  - the answer sufficiently addresses the question  
  - the information is correct and used properly  

---

**Advantages**
- immediate quality checking  
- protection against hallucinations  
- suitable for precise or critical systems  

**Disadvantages**
- increases latency (additional model call)  
- increases cost (more tokens)  
- slower overall system  
- often unnecessary for newer, more reliable models  

---

## Few-Shot Prompting

Using the zero-shot technique usually produces correct results, but it can fail with more complex tasks.  
For more complex tasks, **few-shot prompting** was introduced, which improves output quality by providing examples of the desired format or behavior.

The principle is simple:  
we show the model several input–output examples, and it learns the pattern directly from them.  
This guides the model, reduces ambiguity, and corrects mistakes that often occur in zero-shot prompting.

---

**Example**
Prompt:  
This is awesome! // Negative  
This is bad! // Positive  
Wow, that movie was rad! // Positive  
What a horrible show! // 

---

## Iterative Prompting

Iterative prompting is a structured, step-by-step approach used to refine and optimize the output in more complex tasks or multi-step interactions, where responses must dynamically adapt to evolving inputs. It typically happens in the following steps:

1. **Initial prompt creation**  
   - create a clear initial prompt

2. **Model response evaluation**  
   - review the AI-generated response

3. **Prompt refinement**  
   - modify or extend the prompt based on what was missing or wrong

4. **Feedback incorporation and iteration**  
   - incorporate human or automated feedback to rate the quality of responses  
   - use this feedback to improve the next iteration

## Summarizing

Summarizing is the process of reducing text while keeping the essential meaning.  
With prompts, we can control **length**, **style**, **audience**, or **specific details** the model should extract.

---

**Template**  
Summarize the following text according to the rules below:  
Length: {short | medium | long | number of bullets}  
Style: {neutral | academic | professional | simple}  
Focus: {key ideas | facts | names | dates | deadlines | arguments}

Text:  
"""  
{INPUT_TEXT}  
"""

---

**Examples:**
- **controlled length**  
Summarize in exactly 3 bullet points.
- **controlled audience**  
Explain to a 12-year-old.
- **controlled style**  
Write in a professional tone.
- **extraction summary**  
Extract only dates, names and deadlines.

---

## Inferring

Inferring means deriving new information through deduction or reasoning.  
For an AI model, inferring is the ability to analyze given text and extract implicit meaning, facts, or attributes that are not directly stated but can be logically concluded.  

The model receives input → analyzes it → and infers the required conclusions.

---

**Example**  

**Input:**  
Infer the following information from the <text> and present it in JSON format.  
Information to infer: Sentiment, Anger, Item, Brand  

Text:  
"review of product"

**Output:**  
```json
{
  "Sentiment": "positive",
  "Anger": false,
  "Item": "MacBook",
  "Brand": "Apple"
}



## Transforming

## Expanding

## Chain-of-Thought Reasoning

## Chaining Prompts

## Appendix