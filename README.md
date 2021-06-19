# QnA Web App  

![](web.gif)  

 
## About  

This project implements the work done by Minjoon Seo in BI-DIRECTIONAL ATTENTION FLOW FOR MACHINE COMPREHENSION (https://arxiv.org/pdf/1611.01603.pdf). The paper has addressed machine comprehention task i.e - answering a question query given a context paragraph. In this paper, they have proposed following major changes to conventional unidirectional attention mechanism. 1. Multi-stage hierarchical process that represents context at different level of granularity, that is --> Context text and query text are encoded using character embedding, pre-trained word embedding and contextual embedding layer. 2. Attention mechanism in both direction, query to context and context to query. 3. Attended vector is allowed to **flow** through subsequent layers, this helps to reduce information loss along the layer.  

Model diagram:

 ![image](https://user-images.githubusercontent.com/39105103/121294848-b1d0b380-c90b-11eb-8b5f-f27118d41701.png)  
 
 ### Model Building  
 
 SQUAD 1.0 (https://rajpurkar.github.io/SQuAD-explorer/) Dataset is used to train the model. Model is constrained with inbound queries only that is model will always return text from the given paragraph even if answer doesn't exist in the paragraph. Tool pymagnitude (https://github.com/plasticityai/magnitude) is used as input pipeline for pre-trained glove and fasttext embeddings. And exact same model architecture as above is used to build model.  
 
 
 ![image](https://user-images.githubusercontent.com/39105103/121298086-ea26c080-c910-11eb-9ef2-3a74a119a5e9.png)  
 
 
 ### Deployment  
 
 Model is served using Tensorflow serving. Then it is linked to web application as shown in below flow chart:  
 
 ![image](https://user-images.githubusercontent.com/39105103/121307134-51e30880-c91d-11eb-946a-d20d0508d4af.png)  
 
 Trained model is first saved in tf saved model format then it is served using tensorflow serving docker. REST api is used to pre-process the incoming request and convert the response from docker server into text format. Web app is a UI sending request to REST api.  
 
 
 ## Steps to use it  
 
 #### 1. Train and save the model.  
 
     -  Run 'ML Model/Bidaf' this notebook is self explainatory. It will train and save the model.  
     
     
#### 2. Serve the model using tensoeflow serving docker.  

    -  Install the docker from -https://docs.docker.com/get-docker/  and run 'docker pull tensorflow/serving' this shell command.
    
    -  Start the container and open the API port. File 'docker.sh' contains shell command to get the docker running locally. Refer https://www.tensorflow.org/tfx/serving/docker for more details.  
    
#### 3. Start the REST api.  

    -  Run 'API/rest_api.py' python script. It will create an endpoint.  
    
#### 4. Host the Web app locally.  

    -  Run 'Web app/WebApp.html'. The application is hosted locally now.  
    
Note: Cross check the IPs and path. As they are system dependent.
    
    
## Future work.  

  - Try dynamic attention mechanism.
  - Use BERT
  - Extend it to SQUAD 2.0
     
