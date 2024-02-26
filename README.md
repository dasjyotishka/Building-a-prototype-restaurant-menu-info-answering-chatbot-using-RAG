# RAG-based-restaurant-menu-info-answering-chatbot

This is a protype of a RAG based restaurant menu info answering chatbot. 

# Steps to reproduce
This repo contains a python notebook containing the code and the results obtained after executing the code. Sklearn was used for the modelling steps. To reproduce the code, just execute the cells of the notebook sequentially.

# Evaluation
- Total prompt generation time: < 50ms.
- Accuracy: The model was able to correctly retrieve the correct menus in all of the 7 examples tested.

 # Further improvements
 Since in the general remarks of the task, it was mentioned that LLM is not required for demo, I have mostly focused on the retrieval part and not on the generative part of the RAG.

The possible next steps to get a more fine-tuned answer is to use an LLM. 
A prompt such as "Given a query, whose answers correspond to {{matched_categories}} and {{matched_details}}, generate an answer to it" needs to be build passing the ***matched_categories*** and ***matched_details*** lists in the context. This would ensure that we get a fine-tuned answer to the question even in a very limited context size of the LLM.
