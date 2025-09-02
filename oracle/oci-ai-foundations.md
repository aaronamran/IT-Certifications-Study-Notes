# OCI AI Foundations

## AI Foundations
- AI: Ability of machines to mimic cognitive abilities and problem-solving capabilities of human intelligence
- Commonly used AI domains: Language, Audio and Speech, Vision
- Text Data: Inherently sequential (sentences), multiple words (tokenisation), varying sentence lengths (padding) and similar words (dot or cosine similarity and embedding)
- Language AI Models: Recurrent neural networks, long short-term memory, transformers
- Audio and Speech as Data: Digitised snapshots in time (sample rate), sampling rate of 44.1kHz (sound reconstructed at 44100 times per sec) and bit depth (number of bits in each of the 44100 audio pieces)
- Audio and Speech AI Models: Recurrent neural networks, long short-term memory, transformers, variational autoencoders, waveform models, siamese networks
- Images as Data: Images consists of pixels, pixels are grayscale or color
- Vision AI Models: Convolutional neural networks, YOLO, generative adversarial network
- Deep Learning is a subset of Machine Learning, which is in turn a subset of AI
- ML types: Supervised ML (extracting rules from data), unsupervised ML (extracting trends from data), reinforcement learning (solving tasks by trial and error)
- DL extracts features and rules from data
- Neural networks is made up of interconnected nodes or neurons in a layered structure that resembles the human brain
- Function approximation is a technique for estimating an unknown underlying function using historical observations from the domain
- Gen AI is a subset of ML that produces content (audio, text, code, video, images)


#### Skill Check
- Which type of ML is used in autonomous car driving? Reinforcement Learning
- Which task is an example of a speech-related AI task? Speech-to-text Conversion
- Which task is a Gen AI task? Writing a poem based on a given theme
- Which is NOT an example of vision or image-related AI task? Repair damaged images
- Which type of ML algorithms extracts trends from data? Unsupervised ML



## Machine Learning Foundations
- ML is a subset of AI that focuses on creating computer systems that can learn and improve from experience
- Supervised learning: Classify data or make predictions. Labeled data is used to train the model. Model learns the relation between features and labels
- Unsupervised learning: Understand relationships within datasets. Labels are not used
- Reinforcement learning: Make decisions or choices
- Supervised learning: 2 outputs: regression (continuous) and classification (categorical). Classification can be binary or multi-class
- Classification: A supervised ML technique used to categorise or assign data points into predefined classes based on their features or attributes
- Logistic regression predicts if something is true or false instead of predicting something continuous like house prices. Uses an S-shaped curve (sigmoid function) to fit the data to squash numbers between 0 and 1
- Unsupervised learning: Has no labeled outputs, algorithms learn the patterns in the data and group similar data items
- Clustering is the grouping of similar data items. Data items are more similar within a cluster than items outside it
- Similarity is how close two data points are to each other and is a value between 0 and 1
- Unsupervised learning workflow: Prepare the data (remove missing values, normalise the data and perform feature scaling), create similarity metrics (choose a similarity metric based on nature of data and clustering algorithms used), run clustering algorithm (use the chosen similarity metrics to cluster the data) and interpret results and adjust cleaning (check the quality of your clustering output by verifying against expectations iteratively)
- Reinforcement learning is a type of ML that enables an agent to learn from its interactions with the environment and receives feedback in the form of rewards or penalties, without any labeled dataset. Used in autonomous vehicles, smart devices, industrial automation and gaming and entertainment
- RL Terminology: Agent (Interacts with environment, takes actions, learns from feedback), Environment (External system with which the agent interacts), State (Representation of the current situation of the environment at a particular time), Action (Possible moves or decisions that the agent can take in each state) and Policy (Mapping that the agent uses to decide which action to take in a given state)


#### Skill Check
- Which algorithm is used for predicting continuous numerical values? Linear regression
- Which type of function is used in Logistic Regression to predict a loan defaulter? Sigmoidal function
- Which type of ML algorithm learns from outcomes to make decisions? Reinforcement learning
- What type of ML algorithm is used when we want to predict the resale price on a residential property? Regression
- Which application does NOT require a ML solution? Password validation



## Deep Learning Foundations
- Deep Learning (DL) is a subset of ML that focuses on training Artificial Neural Networks (ANN) with multiple layers and allows them to auto-learn and extract intricate representations from data
- ML needs us to specify features. DL extracts features from raw and complex data. Internal representation of data is built using extracted features. DL algorithms allow parallel processing of data which leads to better scalability and performance
- ANN Building Blocks: Layers (Input, hidden, and output layers receive inputs, transform it, and produce output), Neurons (Computational unit from an input and produces an output), Weights (Determines the strength of connection between neurons), Activation Function (Works on the weighted sum of inputs to a neuron and produces an output), Bias (Additional input to a neuron that allows certain degree of flexibility)
- ANNs are trained using Backpropagation Algorithm (Guess and compare > measure the error > adjust the guess > update the weights > repeat)
- Sequence Models: Input data is in the form of sequences. The goal is to find patterns and make predictions
- Recurrent Neural Networks (RNN): Handles sequential data, allows information to persist using feedback loop, maintains a hidden state or memory and captures dependencies
- RNN architecture: One-to-one (Standard non-sequential data like FNN), one-to-many (music generation or sequence generation), many-to-one (sentiment analysis based on reviews), many-to-many (machine translation and named entity recognition)
- Long Short-Term Memory: Works by using a specialised memory cell and gating mechanisms to capture long-term dependencies in sequential data. Selectively remembers or forgets information over time
- LSTM process: Input Processing (Inputs current data point in the sequence) > Previous Memory (Receives the previous hidden state values) > Gating Mechanism (Is the core of LSTM: Input gate, Forget gate, Output gate) > Updating Memory (Updates the cell state by using the information of input gate and forget gate) > Output Generation (Generates the output of LSTM for current time step)
- DL Models: Feed Forward Neural Networks (FNN), Convolutional Neural Networks (CNN), Recurrent Neural Networks (RNN), Autoencoders, Long Short-Term Memory (LSTM), Generative Adversarial Networks (GAN), Transformers
- CNN: Processes grid-like data, reduces images into an easier-to-process form
- CNN Layers: Input Layer (Accepts 3D images with height, width, and depth representing RGB color channels), Feature Extraction Layers (Repeating pattern of convolution layer with ReLu activation function and a pooling layer) and Classification Layers (Fully connected output layer, where classification occurs)
- Feature Extraction Layers: Auto-learns and extracts relevant patterns and features from the input images. Convolution Layer (applies convolutional operations to the input image using small filters known as kernels), Activation Layer (allows the network to learn more complex and non-linear relationships in the data), Pooling Layer (Helps reduce the computational complexity and also the spatial dimensions of the feature maps generated by the convolutional layers)
- Limitations of CNN: Requires massive data and computations, susceptible to overfitting due to limited training data, difficult to interpret (black box models), sensitive to small input changes
- Applications of CNN: Image classification, object detection, image segmentation, face recognition, medical imaging, autonomous vehicles, remote sensing


#### Skill Check
- Which sequence model can maintain relevant information over long sequences? LSTM NN
- Which essential component of Artificial Neural Network performs weighted summation and applies activation function on input data to produce an output? Neuron
- Which Neural Network has a feedback loop and is designed to handle sequential data? Recurrent Neural Networks
- How do hidden layers in neural networks help with character recognition? Enabling the network to learn complex features like edges and shapes
- Which type of RNN architecture is used for Machine Translation? Many-to-many



## Generative AI and LLM Foundations
- Gen AI: subset of DL where models are trained to generate own output. Learns the underlying patterns in a given data set and uses that knowledge to create new data that shares those patterns
- Inference: process of getting a new prediction by giving a new data point
- ML: learns relationship between data and label, output is label
- Gen AI: learns patterns in unstructured content, output is new content
- Applications of Gen AI: Image and video generation, creative content generation, data augmentation and synthesis, medical imaging and drug discovery, natural language processing
- Language Model (LM) is a probabilistic model of text
- Parameters: Adjustable weights in the model's neural network. More paramters = more capacity = can fit a more complex set of patterns in the data it was trained on
- Model size: Memory required to store the model's parameters. Too large parameters can make model overfit on training data
- RNN handles sequential data, allows information to persist using a feedback loop and maintains a hidden state or memory and captures dependencies
- Transformers can look at all the words in the sentence at the same time and understand how they relate to each other
- Attention Mechanism adds context to the text. Encoder processes input and encodes it into embeddings, decoder generates output
- LM understands tokens rather than words
- Embeddings are numerical representations of a piece of text converted to number sequences, which makes it easy for computers to understand relationships between pieces of text
- Embeddings use case (RAG): User's question is encoded as a vector and sent to a Vector DB. Vector DB finds private content that closely match the user's question. The content is sent to the LLM to help answer the user's question. LLM uses the content plus general knowledge to provide an informed answer
- Transformer model types: Encoder only (Semantic search), Decoder only (Text Generation), Encoder-Decoder (Machine Translation)
- Prompt Engineering: Process of iteratively refining a prompt for the purpose of eliciting a particular style of response
- Aligning LLMs to follow instructions: Completion LLMs are trained to predict the next word on a large dataset of internet text, rather than to safely perform the language task that the user wants. You cannot give instructions or ask questions to a completion LLM, instead need to formulate your input as a prompt. Instruction tuning is a critical step in LLM alignment, it involves fine-tuning a pre-trained LLM on a varied set of instructions, each paired with a desired output
- In-context learning: conditioning (prompting) an LLM with instructions and or demonstrations of the task it is meant to complete
- K-shot prompting: explicitly providing K examples of the intended task in the prompt
- Few-shot prompting is believed to improve results over 0-shot prompting
- Chain-of-thought prompting: provide examples in a prompt to show responses that include a reasoning step
- RAG: Language model can query enterprise knowledge bases to provide grounded responses, does not require fine tuning
- LLM Fine-tuning by taking a pretrained foundational model and providing additional training using custom data. Inference is model taking a new text as input and generates output text based on what it has learned during pretraining and fine-tuning
- Fine-tuning a pretrained model: Optimise a model on a smaller domain-specific dataset. Recommended when a pretrained model doesn't perform your task well or when you want to teach it something new


#### Skill Check
- What aspect of LLM significantly impacts their capabilities, performance, and resource requirements? Model size and parameters, including the number of tokens and weights
- Sequence models are used to solve problems involving sequentially ordered data points or events. Which is NOT the best use case for sequence models? Image classification and object recognition
- Fine-tuning is unnecessary for LLM if your application does not involve which specific aspect? Task specific adaptation
- What is "in-context learning" in the context of LLMs? Providing a few examples of a target task via the input prompt
- Which statement accurately describes generative AI? Creates new content without making predictions



## OCI AI Portfolio
- Oracle AI Stack: Business Apps, Oracle SaaS Portfolio: OCI Gen AI, Digital Assistant, Speech, Language, Vision, Document Understanding. ML Services: OCI Data Science, ML in Oracle DB, Data Labelling. AI Infrastructure: Compute Bare Metal Instances and VMs, Cluster Networking, Block, Object, and File Storage, HPC, Filesystems
- Ways to access OCI AI Services: OCI Console, REST API, Language SDKs, CLI
- OCI AI Services: Language (Pretrained Models, Custom Models, Text Translation), Vision (Image Analysis Pretrained Model/Custom Model), Speech (Transcription), Document Understanding (OCR, Text Extraction, Key Value Extraction, Table Extraction, Document Classification), Digital Assistant
- OCI Data Science: Cloud service focused on serving data scientists throughout the full ML life cycle with support for Python and open-source libraries
- OCI Data Science Core Principles: Accelerated, Collaborative, Enterprise-grade
- Projects are containers that enables data science teams to organise their work and are collaborative workspaces. Tenancy can as have many projects as needed without limits
- GPU performs simple operations very rapidly and allows parallel computing for higher throughput
- Remote Direct Memory Access (RDMA): data transfer/network communication from one machine to another that bypasses CPU. Low latency, high bandwidth
- RDMA over Converged Ethernet (ROCE): OCI's Ethernet fabric that powers HPC, GPU and DB workloads
- RDMA Supercluster: Designed to scale to tens of thousands of GPUs. Fabric uses a three-tier Clos topology (non-blocking interconnect). Latency within a block (6.5 µs round trip) and across blocks (20 µs round trip). Uses lossless networking (no dropped packets) and uses intelligent congestion control and switch buffering tuned for higher latency paths
- AI Ethics Principles: Respect for human autonomy (Human centric and allow human oversight), Prevention of harm (technical robustness and safety, privacy and data governance), fairness (transparency, diversity, nondiscrimination, fairness)


#### Skill Check
- Which OCI Data Science feature enables you to define and run repeatable ML tasks on fully manageed infra? Jobs
- Which data type is used in Oracle DB 23ai to compare documents? Vector
- Which OCI Data Science feature allows you to use catalogued models as HTTP endpoints on fully managed infra? Model Deployments
- Which is NOT an OCI AI service? Translator
- What is the advantage of using OCI Superclusters for AI workloads? Deliver exceptional performance and scalability for complex AI tasks



## OCI Generative AI Service
- Fully managed service that provides set of customisable LLMs available via a single API to build gen AI apps. Have models such as Meta and Cohere. Flexible fine-tuning using own dataset and has dedicated AI clusters
- Pretrained Foundational Models: Chat (ask questions and get conversational responses) and Embedding (convert text to vector embeddings semantic search)
- Oracle DB 23ai: SQL support for vector generation, Vector data type, similarity search with SQL syntax and functions, approximate search indexes
- Vector Distance Function: to gauge similarity, distance between 2 vectors is smaller for entries that are more similar
- Select AI: query data directly using any language. Translates natural language into Oracle SQL language


#### Skill Check
- 




## OCI AI Services

#### Skill Check



