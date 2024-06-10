# LLMs: Beyond Chat

This tutorial covers using [Pydantic](https://docs.pydantic.dev/) and [Instuctor](https://python.useinstructor.com/) with OpenAI GPT-4o to use the LLM as a software device for implementing different tasks.

- **Notebook**:
  - [llms-beyond-chat.ipynb](llms-beyond-chat.ipynb) - the notebook with complete solutions and outputs.
  - [llms-beyond-chat---practice.ipynb](llms-beyond-chat---practice.ipynb) - the tutorial notebook with solutions and outputs ommitted. Use this version to complete the tutorial yourself.

To run: `cp dot.env .env`, update the variables to an Azure Open AI GPT-4o, and launch with Jupyter.

*You can use older GPT-4 versions without a problem (they're just slower and more expensive), or use a standard OpenAI endpoint by substituting the `AzureOpenAI` object with an `OpenAI` object from the OpenAI SDK.*