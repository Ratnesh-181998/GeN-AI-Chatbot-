- Gen AI Chatbot

1.RAG based virtual assistant is developed using AWS Cloud Formation template
2. In this we have configured CloudFormation template with chunking type- hierarchical(parent-child relationship), vector embedding type- semantic, guardrail, synonyms. Embedding Model- Embed English v3(transformer based not LLM based), text generation - Mixtral 8*7b llm model , vector dimension = 1024. 
:
1.	Store gem information in S3 bucket
2.	Develop a chatbot solution through deployment dashboard - it creates a stack (combination of multiple services) through cloudformation template, it has a combination of all the required AWS services so that all services not be initialized separately. In deployment dashboard, specify the llm model parameters- temperature =0, top_k = 0.9 , top_p .Choose resources and configure embedding type, guardrail, synonyms, stop sequence. And specify the prompt.
3.	Configure amazon kendra for crawling the urls/pdfs ,embedding and vector indexing and storing it - opensearch.
4.	Used LLM Model through AWS Bedrock to generate the response of user queries and the information stored in cloudformation template, user query and the knowledgebase is the input to the LLM model to generate the user query response
5.	Dynamo db stores the user conversations which helps to identify the context of upcoming query. It also stores the Logs (also it is used for identifying the context ) which can be visualised through multiple dashboards in cloudwatch
6.	Aws cognito service is used for user authentication and api gateway is used to connect the socket connection
7.	Serverless Lambda is used to invoke the cognito service and llm model through langchain
8.	WAF is used for security to prevent vulnerabilities - By cloudwatch we are monitoring the number of IP hits in the chatbot. If any particular IP hits are more than expected at a specific time, then that IP is given to Security team for monitoring.
![Gen AI Chatbot Architectures Diagram](https://github.com/user-attachments/assets/d376796b-b29f-49ee-8ac2-c9d09d4c55ce)
