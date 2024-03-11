# RAG-based-restaurant-menu-info-answering-chatbot

This is a protype of a RAG based restaurant menu info answering chatbot. A demo restaurant menu is provided in a JSON file. The objective of this project is to use a RAG based question answering chatbot to reply to the user's question. In real life, this menu might be much bigger with more options. Hence, in order to save on tokens for the prompt, a RAG is used to retrieve the informations from the menu. The relevant informations can then be passed to an LLM to generate the desired output.

# Steps to reproduce
This repo contains a python notebook containing the code and the results obtained after executing the code. Sklearn was used for the modelling steps. To reproduce the code, just execute the cells of the notebook sequentially.

# Design choice
The design choice was dependent on the speed of execution of the query. Using only an LLM for designing this problem would have invited a lot of computational complexity, and thereby a slower response rate. Using a RAG can help us speed up the response rate. RAG is also less prone to hallucinations and biases since is has a deterministic way to retrieve a result and generate inference from it.

During the retrieval phase, the most important information to vectorize was found to be the name of the menu items. Hence, the names of the items were stored in a list. Another list was created to store all the details of the different items available. The items names were vectorized to make it useful in searching for the relevant matches. Then, a vector database was created storing the details of the menu along with the vectorized item names. During the evaluation phase, the query was vectorized and the cosine similarity between the vectorized query and the vectorized item name was calculated. If the similarity was more than a threshold value (0.71), the item name and its details were added in an empty list. The threshold value was selected after checking the accuracy of the results for it from the example queries. Based on the items shortlisted, the response was then generated.

# Evaluation
- Total prompt generation time: < 50ms.
- Accuracy: The model was able to correctly retrieve the correct menus in all of the 7 examples tested.

 # Fine Tuning
The possible next steps to get a more fine-tuned answer is to use an LLM. A prompt such as "Given a query, whose answers correspond to {{matched_categories}} and {{matched_details}}, generate an answer to it" needs to be build passing the ***matched_categories*** and ***matched_details*** lists in the context. This would ensure that we get a fine-tuned answer to the question even in a very limited context size of the LLM.
