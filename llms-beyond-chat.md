# LLMs: Beyond Chat

## *AI as Software / LLM as a VM*

- Eleanor Berger <eberger@microsoft.com>
- Sandip Kulkarni <sakulka@microsoft.com>
- Alexandra Savelieva <alsavelv@microsoft.com>

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
- Keeps the human in the loop

---

# Chat is Not Enough: UX

- Chat is a great user experience … until it isn’t​
- “Chat Fatigue”: it’s exhausting to chat all the time​
- People are multi-modal​  
	The best user experiences combine the textual with visual, audible, tactile​
- Good UX helps users form habits

---

# Chat is Not Enough: Integration

- Human in the loop is a great solution for easy integration​
- Human in the loop is inefficient
- Human in the loop is expensive
- Human in the loop is error-prone
- The promise of AI is autonomy

---

# Chat is Not Enough: Business

- Chat systems are generic AI capabilities​
- Good general AI capabilities are hard and expensive to build​  
	The biggest players (OpenAI, Microsoft, Google, Meta, …) are hard to compete with​
- “OpenAI killed my startup”​  
	The ChatGPT for _____ is … ChatGPT​  
	The Copilot for _____ is … Copilot​
- Startups and enterprises can win with AI when they focus on unique, domain-specific, differentiated capabilities

---

# How to AI as Software: Process Mapping

- Learn to view the world as a collection of well-defined processes​
- Break processes down to the smallest discreet operations possible
- Determine input and output for each operation, and the transformation it needs to achieve
- Identify which operations can be performed using GenAI​
- Process Mapping is the new Prompt Engineering

---

# How to AI as Software: Technical Implementation

- Master using the LLM as a new kind of VM​ 
	
	JVM/CLR/...: Code -> Functions​
	
	LLM: Prompt/Definitions -> (intelligent) Functions​
- LLMs can do things that are hard or impossible to do with traditional software … and are easy to “program”
- Use structured input and output (JSON, ....)​  
	Helps bridge between traditional software and AI​  
	Set clear schema, validation rules

---

# Why AI as Software: Deep Integration

- Deep integration with your product / processes / UX​
- Differentiate and use AI to amplify your unique advantages​
- (Limited) autonomy is possible

---

# Why AI as Software​: Security

- Divide and conquer
- Control and secure AI by breaking things down and reducing the surface area for attacks
- Add guardrails specific to each invocation

---

# Why AI as Software: Reliability

- Achieve reliable and predictable results using hard to control AI
- Design, develop, and test each operation in isolation to guarantee predictable and reliable behaviour
- Observability - monitor and understand your system just as you do traditional software systems

---

# Why AI as Software: Choice

- Use the model with the best cost / performance / capabilities / licensing / customisation for each operation
- Many operations can be performed with smaller models like Phi-3 (or GPT-3.5, Mistral, Llama, ...) at better speed and cost
- Some operations require the intelligence of a frontier model
- LLMs are stateless by default, so use the best model for each operation
- Evaluating which model works best is a lot easier on per-operation basis

---

# Tutorial - AI as Software / LLM as a VM

- We'll explore several simple examples of using LLMs for different tasks
- We'll be using GPT-4o for everything, just to keep things simple - many of these examples can work just as well with simpler models
- We'll be relying primarily on defining schemas (with Pydantic) and getting the LLM to use them (using Instructor) to figure out what to do; Very little prompting - most of the power comes from the definitions
- These examples are small and simple, but if you master this approach to working with LLMs you'll find that it is applicable to many powerful use-cases

---

# Some Other Zhings to Explore

- Structured Input / Output & Control
	- Instructor
	- LQML
	- Outlines
	- Magnetic
	- Guidance
- DSPy (optimising compiler for prompting)
- Agents
	- AutoGen
	- LangGraph
	- CrewAI

---

# Setup

1. Create a deployment of GPT-4o (other GPT-4 versions are OK too)
2. Find the tutorial repository at **[aka.ms/llms-beyond-chat](https://aka.ms/llms-beyond-chat)** and clone it
3. Copy `dot.env` to `.env`
4. Update `.env` with the values for your deployment
5. There are two versions of the notebook:
	- **llms-beyond-chat**.ipynb - the complete tutorial with solutions and outputs
	- **llms-beyond-chat---practice**.ipynb - the tutorial without solutions or outputs, use this if you want to practice in real time

---