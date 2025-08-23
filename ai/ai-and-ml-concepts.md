# Artificial Intelligence & Machine Learning Concepts

## Attention Mechanism

A neural network component that enables models to dynamically weight different parts of the input sequence based on relevance to a specific task. Central to transformer architectures, it enhances context sensitivity and scalability for sequence modeling.

## Embedding

A dense, low-dimensional vector representation of high-cardinality discrete inputs (e.g. tokens, categories). Embeddings preserve semantic similarity in the vector space and are typically learned jointly with downstream tasks.

## Epoch

One full iteration over the entire training dataset. Used to quantify training cycles; multiple epochs are typically required for convergence.

## Evaluation Metrics

Quantitative measures of model performance, chosen based on task type. Examples: accuracy, precision, recall, F1 (classification); mean squared error (regression); BLEU/ROUGE (language tasks); AUROC (imbalanced binary tasks).

## Feature

An individual input variable used by the model. Features may be engineered or learned, and are selected based on their relevance to the target variable.

## Fine-Tuning

The process of adapting a pre-trained model to a downstream task using a smaller, task-specific dataset. Often involves adjusting the final layers or the entire network depending on the domain gap and data size.

## Gradient Descent

An optimization algorithm that updates model parameters in the direction of the negative gradient of a loss function with respect to those parameters. Common variants include SGD, Adam, and RMSProp.

## Hallucination (in LLMs)

The generation of confident but factually incorrect or unverifiable output by a language model. Results from overgeneralization, distributional mismatch, or insufficient grounding in factual context.

## Inference

The forward pass of a trained model applied to unseen data to produce predictions or generate outputs. Typically optimized for latency and memory efficiency in production.

## Label

The ground truth target associated with an input sample, used in supervised learning to compute the loss during training.

## Loss Function

A differentiable function that quantifies the error between the model's prediction and the true label. Minimizing this function guides the learning process. Examples: cross-entropy, MSE, contrastive loss.

## Model

A parameterized function that maps inputs to outputs. In ML, models learn from data to approximate functions for classification, regression, generation, or control tasks.

## Overfitting

A condition where a model learns spurious correlations or noise in the training data, resulting in poor generalization to unseen data. Detected via a divergence between training and validation performance.

## Prompt Engineering

The systematic design and refinement of input text to steer the behavior of large language models in a zero-shot or few-shot setting. Often necessary due to the lack of gradient access in inference-only deployments.

## Reinforcement Learning

A paradigm where an agent learns to take actions in an environment to maximize cumulative reward, typically via interaction and feedback. Core elements include state, action, reward, and policy.

## Supervised Learning

A learning paradigm where the model is trained on labeled input-output pairs. The objective is to generalize from training data to accurately predict outputs on unseen inputs.

## Tokenization

The process of segmenting raw input (usually text) into discrete units (tokens) for model processing. Token granularity varies by tokenizer (character, wordpiece, byte-pair encoding).

## Transformer

A deep learning architecture that uses self-attention mechanisms to process sequences in parallel. It replaces recurrence and convolution, enabling efficient modeling of long-range dependencies.

## Training

The iterative process of adjusting model parameters to minimize a loss function over a training dataset. Involves forward passes, backpropagation, and optimization.

## Underfitting

Occurs when a model lacks the capacity to capture the underlying structure in the data. Characterized by high bias and poor performance on both training and validation sets.

## Unsupervised Learning

A paradigm where models infer structure from unlabeled data. Common tasks include clustering, dimensionality reduction, and generative modeling.

## Vectorization

The process of representing input data as numerical vectors to enable mathematical operations in machine learning models. For text, this often precedes embedding and can be sparse (e.g., TF-IDF) or dense (e.g., learned embeddings).

## Zero-Shot Learning

A generalization capability where a model performs a task without explicit task-specific training, relying on prior knowledge encoded during pretraining and appropriate prompting or conditioning.
