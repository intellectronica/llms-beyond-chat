# LLMs: Beyond Chat

## *AI as Software / LLM as a VM*

- Eleanor Berger `<eberger@microsoft.com>`
- Sandip Kulkarni `<sakulka@microsoft.com>`
- Alexandra Savelieva `<alsavelv@microsoft.com>`

June 2024

---

# Pattern: Chat -> AI as Software

- __2022__: GPT-3 … but no-one cares​
- __2023__: ChatGPT … and now it’s all about chat​

	Chat is not going anywhere​

	It’s still the killer app for LLMs​

	But…​
- __2024__: LLMs can do so much more than chat …​
	
	because LLMs are a new way to do software

---

# Why Chat?

- Intuitive
- Easy to integrate
- Keeps the **human in the loop**

---

# Chat is Not Enough: UX

- Chat is a great user experience … until it isn’t​
- **“Chat Fatigue”**: it’s exhausting to chat all the time​
- People are multi-modal​

	The best user experiences **combine the textual with visual, audible, tactile​**
- Good UX helps users **form habits**

---

# Chat is Not Enough: Integration

- **Human in the loop** is a great solution for easy integration​
- Human in the loop is **inefficient**
- Human in the loop is **expensive**
- Human in the loop is **error-prone**
- The promise of AI is **autonomy**

---

# Chat is Not Enough: Business

- Chat systems are **generic AI capabilities**​
- Good **general AI capabilities are hard** and expensive to build​  
	The biggest players (OpenAI, Microsoft, Google, Meta, …) are **hard to compete with**​
- *“OpenAI killed my startup”​  *
	The ChatGPT for _____ is … ChatGPT​
	The Copilot for _____ is … Copilot​
- Startups and enterprises can win with AI when they **focus on unique, domain-specific, differentiated** capabilities

---

# How to AI as Software: Process Mapping

- Learn to **view the world as a collection of well-defined processes**​
- **Break processes down** to the smallest discreet operations possible
- Determine **input and output** for each operation, and the **transformation** it needs to achieve
- **Identify which operations** can be performed using GenAI​
- **Process Mapping** is the new Prompt Engineering

---

# How to AI as Software: Technical Implementation

- Master using **the LLM as a new kind of VM**​ 
	
	**JVM/CLR/...**: Code -> Functions​
	
	**LLM**: Prompt/Definitions -> (intelligent) Functions​
- LLMs can do t**hings that are hard or impossible to do with traditional software** … and are easy to “program”
- Use **structured input and output** (JSON, ....)​  
	Helps bridge between traditional software and AI​  
	Set clear schema, validation rules

---

# Why AI as Software: Deep Integration

- **Deep integration** with your product / processes / UX​
- **Differentiate** and use AI to amplify your unique advantages​
- **(Limited) autonomy** is possible

---

# Why AI as Software​: Security

- **Divide and conquer**
- Control and secure AI by *breaking things down* and **reducing the surface area** for attacks
- Add **guardrails** specific to each invocation

---

# Why AI as Software: Reliability

- Achieve **reliable and predictable results** using hard to control AI
- Design, develop, and test **each operation in isolation** to guarantee predictable and reliable behaviour
- **Observability**: monitor and understand your system just as you do traditional software systems

---

# Why AI as Software: Choice

- Use the model with the **best cost / performance / capabilities / licensing / customisation** for each operation
- Many operations can be performed with **smaller models like Phi-3 (or GPT-3.5, Mistral, Llama, ...)** at better speed and cost
- Some operations require **the intelligence of a frontier model**
- LLMs are **stateless** by default, so use **the best model for each operation**
- **Evaluating** which model works best is a lot easier on per-operation basis

---

# Tutorial - AI as Software / LLM as a VM

- We'll explore several **simple examples of using LLMs for different tasks**
- We'll be using **GPT-4o for everything**, just to keep things simple - many of these examples **can work just as well with simpler models**
- We'll be relying primarily on **defining schemas (with Pydantic)** and **getting the LLM to use them (using Instructor)** to figure out what to do; Very little prompting - most of the power comes from the definitions
- These examples are small and simple, but **if you master this approach to working with LLMs you'll find that it is applicable to many powerful use-cases**

---

# Some Other Zhings to Explore

- **Structured Input / Output & Control**
	- Instructor
	- LQML
	- Outlines
	- Magnetic
	- Guidance
- **DSPy** (optimising compiler for prompting)
- **Agents**
	- AutoGen
	- LangGraph
	- CrewAI

---

# Setup

1. **Create a deployment of GPT-4o** (other GPT-4 versions are OK too)
2. Find the tutorial repository at **[aka.ms/llms-beyond-chat](https://aka.ms/llms-beyond-chat)** and **clone it**
3. Copy `dot.env` to `.env`
4. Update `.env` with the values for your deployment
5. There are two versions of the notebook:
	- **llms-beyond-chat**.ipynb - the complete tutorial with solutions and outputs
	- **llms-beyond-chat---practice**.ipynb - the tutorial without solutions or outputs, use this if you want to practice in real time

---

# Setting up Azure Open AI, Instructor, and Helper Functions

- **Instructor** patches the OpenAI client to return a Pydantic model (inherits from BaseModel)
- The `llm()` function **calls the LLM API with a model**, for schema definition and output
- `print_schema`, `print_result`, `visualize_graph`, and `print_tree` for printing things nicely in the notebook

---

# Working with Text: Translation

- These examples are completed in both notebooks - to help us get used to the format we'll use throughout the tutorial
- Look at the **model**, and how it is **translated into a JSON schema** (this is the schema that is being passed to the API)
- See how **we can complete the task with very little prompting** and get the result as an instance of the model
- The **`List`** and **`Enum`** types of Python are useful for more complex structure
- A convention we'll often use - s**ystem prompt for "programming"**, **user promt for "input"** *(just a convention)*

---

# Working with Text: Normalisation

- If you're using the practice notebook, now you can **start writing your own calls**
- Translation between languages or between styles within the same language is more-or-less the same thing
- So you already know how to complete this task
- *remember that you can always look at the master notebook and compare your solution*

---

# Unstructured Data: Parsing Addresses

- Look at the first example. **No prompting!** We can get a lot done with just a good schema definition.

  *Don't expect to complete all examples with no prompting at all, though*
- Parsing many addresses is just about as simple as doing one.

---

# Unstructured Data: Building a Knowledge Graph

- With **minimal prompting and a good schema definition**, we can get the LLM to build a knowledge graph representation of the information in the text.
- Remember that you can use the **`visualize_graph`** function to render a graphic in the notebook. It expects a graph object, that has two lists: nodes, and edges.

---

# Unstructured Data: Parsing a Grammar Tree

- This used to be a **serious challenge in computational linguistics**, but is actually easy for an LLM.
- It's a more **complex structure, where we have nested elements** and potentially recursion.
- A simplified grammar tree of the sentence `the quick brown fox jumps over the lazy dog` would be something like:
  - Verb Phrase
	  - Noun Phrase
		  - Determiner: *the*
			- Adjectives:
			  - *quick*
				- *brown*
			- Noun: *fox*
		- Verb: *jumps*
		- Preposition Phrase
			- Preposition: *over*
			- Noun Phrase:
				- Determiner: *the*
				- Adjectives:
					- *lazy*
				- Noun: *dog*

---

# Synthetic Data Generation

- Generating data on demand is incredibly **valuable for training and evaluation projects**
- Easy when you can control precisely the parameters and format of what you're generating

---

# Decision Making: Sentiment Analysis

- Sentiment Analysis is a form of decision-making. We need to **pass judgement on a piece of data**.
- The LLM exhibits "self reflection" (only by analogy) when it is able to also estimate its own confidence in a decision.
- Similar tasks are very common and present a great opportunity to use LLMs for automation and decision support.

---

# Decision Making: Classification

- Classification (in this case, assigning tags to items) is also a form of decision-making
- Note that we are relying on both **constraints that we introduce in the request**, and **knowledge of the world that is already available to the model**
- In more complex scenarios, **where we can't rely on knowledge that is "baked into" the model**, we might need to pr**ompt with a lot more detail and use in-context learning**.

---

# Decision Making: Clustering

- **Clustering**, as an example, is interesting, because it **contrasts** with implementations that use **predictive** AI/ML
- What the LLM can do easily, which isn't straightforward to do with predictive AI, is **explain** its choices (in this case, by giving each cluster a title)
- **We may have more confidence in an AI system** and give it more freedom to operate autonomously **if we understand** why it is making the choices it does

---

# Planning

- A lot of interesting processes can't be completed using a hard-coded recipe and require some planning
- In this example, **the LLM is quite good at planning** how to use different actions at the correct order for different scenarios
- **Agent systems** often rely on planning phases to break down the work to steps

---

# Shall We Play a Game?

- **Tic-tac-toe** doesn't require a lot of intelligence, in fact it is easy to implement with traditional coding, but it serves as a good simple example
- **The LLM is doing all of the heavy lifting** like assessing the state of the game and deciding on the next move based on a defined strategy
- LLMs have been shown to play Chess well, as well as games that aren't part of the training (with good prompting)
- By **interacting with part of the world outside the LLM** (the tic-tac-toe board, in this case), we can automate a cognitive task

---

# Summary

- AI is Software
- LLMs are a new kind of VM
- Using structured input/output we can get LLMs to do really useful things

## Some ideas for followup

- Try these or similar examples with other LLMs (Phi-3, GPT-3.5, Llama-3, Mixtral, ...)
- Identify more complex tasks you can achieve with this approach. How much can you rely on definitions? When do you need to invest more in prompting?
- How can you evaluate and test your integrated solution? With very clear input and output it should be straightforward to test and gain confidence in the accuracy and reliability of your system.

---