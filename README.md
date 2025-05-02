# AWS-Multi-Agent-Workshop
Infosys Lg one workshop

What we are building
You now should be in your SageMaker Notebook Instance and see the repository copied in Jupyterlab. To proceed with running the notebook move to the next page. All information shown here is also in your Jupyter Notebook.

This build session will show you how to build an agentic services with orchestration for reasoning, powered by Foundation models on Amazon Bedrock. We will use a KnowledgeBase  backend, which will retrieve context documents for our booking service.

While you can have a single RAG database you index your documents in, often companies will have multiple databases that contain different topics. For example, an airline may have their customer service documents in one database, and then documentation on their planes in a separate database. For scenarios like this, we want our LLM to be able to route to the correct database to find the right context.

Let's look at the architecture for what we are building:

Image
![image](https://github.com/user-attachments/assets/f2d5a313-5260-4380-907b-3438d68333bf)


The system employs a modular architecture with various agents, databases, and evaluation components to process and respond to user inputs. The main components include:

Prompt Rewrite
Router
Specialized Agents
Graders
Knowledge Base and Databases
Human Intervention
Flow Description
Start: The process begins when a user input is received.
Prompt Rewrite: The initial input undergoes a prompt rewrite step, potentially to optimize or standardize the query.
Router: The rewritten prompt is sent to a router, which determines which specialized agent(s) should handle the query.
Specialized Agents: The system includes several agents, each designed for specific tasks:
Bedrock Agent
Langchain Agent
RAG (Retrieval-Augmented Generation) Agent
Search Agent
Multi-modal Agent
5.Knowledge Base and Databases:
OpenSearch (S3): Used for storing and retrieving information
KnowledgeBase: A centralized repository of information
DynamoDB: A NoSQL database accessed via Lambda functions
6. Graders: The output from the agents is evaluated by three graders:
Grader - Hallucination: Checks for fabricated or incorrect information
Grader - Trustworthy: Evaluates the reliability of the information
Grader - Relevancy: Assesses how well the response addresses the query
7. Acceptability Check: The graded responses are then checked for acceptability.
If acceptable: The response is sent to the end of the process.

If not acceptable: The query is redirected to a human for review or intervention.

End: The process concludes with either an AI-generated response or human-reviewed answer.
Additional Components
Lambda: Used for serverless compute, likely for processing or transforming data.
Retry: Associated with the Search Agent, possibly for handling failed searches or refining results.
Usage
This architecture is designed to handle a wide range of queries by leveraging specialized agents and ensuring quality through multiple evaluation steps. It's suitable for applications requiring high accuracy, trustworthiness, and the ability to handle complex, multi-modal inputs.

**Enable:
check the following models
Claude 3 Haiku
Claude 3 Sonnet
Titan Text Embeddings V1
Titan Image Generator G1 v2
Llama 3.1 70B Instruct
Mistral Large 2 (24.07)


Run the notebook
The repository should already be copied into your SageMaker Jupyter notebook. You can open up the Bedrock Agent and KnowledgeBase preparation notebook by clicking on create-agent-with-knowledge-base-and-action-group.ipynb.

Check id Amazon Bedorck KnowledgeBase has been prepared by the CloudFormation template
Sync-up restaurant manus stored in S3 with the KnowledgeBase
Create a Amazon Bedrock Agent and
Associate the Agent with KnowledgeBase
After that you might start to execute reasoning_with_langgraph_bedrock.ipynb.


![image](https://github.com/user-attachments/assets/49cd8c56-98ab-4b5b-bb52-a97093859bc4)


