# QnA Web App
 
## About  

This project implements the work done by Minjoon Seo's BI-DIRECTIONAL ATTENTION FLOW FOR MACHINE COMPREHENSION (https://arxiv.org/pdf/1611.01603.pdf). The paper has addressed machine comprehention task i.e - answering a question query given a context paragraph. In this paper, they have proposed following major changes to conventional unidirectional attention mechanism. 1. Multi-stage hierarchical process that represents context at different level of granularity, that is --> Context text and query text are encoded using character embedding, pre-trained word embedding and contextual embedding layer. 2. Attention mechanism in both direction query to context and context to query. 3. Attended vector is allowed to **flow** through subsequent layers, this helps to reduce information loss along the layer.  

Model diagram:

 ![image](https://user-images.githubusercontent.com/39105103/121294848-b1d0b380-c90b-11eb-8b5f-f27118d41701.png)  
 
 ### Model Building  
 
 SQUAD 1.0 (https://rajpurkar.github.io/SQuAD-explorer/) Dataset is used to train the model. Model is constrained with inbound queries only- model will always return text from the given paragraph even if answer doesn't exist in the paragraph. Tool pymagnitude (https://github.com/plasticityai/magnitude) is used as input pipeline for pre-trained glove and fasttext embeddings. And exact same model architecture as above is used to build model.  
 
 
 ![image](https://user-images.githubusercontent.com/39105103/121298086-ea26c080-c910-11eb-9ef2-3a74a119a5e9.png)  
 
 
 ### Deployment
