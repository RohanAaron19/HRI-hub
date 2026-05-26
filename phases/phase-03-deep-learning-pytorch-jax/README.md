# Phase 03 -- Deep Learning + PyTorch + JAX

> **Time estimate:** 6-8 weeks  
> **Rule:** Every concept has a Quick Quiz. Every 3-4 concepts has a Mini Assignment. Do not watch passively -- pause and answer the quiz before continuing.

---

## Section 1 -- Neural network fundamentals

| # | Concept | Video | Quick quiz |
|---|---------|-------|-----------|
| 3.1 | Neurons, layers, forward pass | [3Blue1Brown -- Neural Networks Ch 1](https://www.youtube.com/playlist?list=PLZHQObOWTQDNU6R1_67000Dx_ZCJB-3pi) | What does a single neuron compute? Write the equation: output = ? |
| 3.2 | Backpropagation and the chain rule | [3Blue1Brown -- Neural Networks Ch 3-4](https://www.youtube.com/playlist?list=PLZHQObOWTQDNU6R1_67000Dx_ZCJB-3pi) | What does backpropagation compute? Why do we need the chain rule? |
| 3.3 | Activation functions: ReLU, sigmoid, tanh, GELU, softmax | [3Blue1Brown -- But what is a neural network?](https://www.youtube.com/watch?v=aircAruvnKk) | Why is ReLU preferred over sigmoid for hidden layers? What problem does sigmoid cause in deep networks? |
| 3.4 | Loss functions: MSE, cross-entropy, focal loss | [StatQuest -- Cross Entropy and Loss functions](https://www.youtube.com/watch?v=Skc8nqJirJg) | Why is cross-entropy used for classification instead of MSE? What happens to the loss when true label=1 and prediction=0.001? |

> **Mini Assignment 3.1 -- Build a neuron from scratch:** Without any ML library, implement a single neuron: (1) forward pass: output = sigmoid(w·x + b), (2) compute loss = MSE(output, target), (3) compute dL/dw and dL/db by hand using chain rule, (4) update w and b with gradient descent. Train it to learn the AND gate. Show every calculation step.

| # | Concept | Video | Quick quiz |
|---|---------|-------|-----------|
| 3.5 | Optimizers: SGD, momentum, Adam, AdamW | [Andrej Karpathy -- optimizers from scratch](https://www.youtube.com/watch?v=mdKjMPmcWjY) | What are the two moment estimates Adam maintains? Why does Adam work better than SGD on sparse gradients? |
| 3.6 | Regularization: dropout, batch norm, layer norm, weight decay | [StatQuest -- Dropout and Batch Norm](https://www.youtube.com/watch?v=NhZVe76DFOM) | What does batch normalization do to each layer's inputs? Why does it help training? What does dropout do during inference? |
| 3.7 | Weight initialization: Xavier, He, orthogonal | [Andrej Karpathy -- weight initialization](https://www.youtube.com/watch?v=jKuhb_e_wPg) | Why does all-zero initialization fail? What does He initialization scale by and why? |
| 3.8 | Vanishing and exploding gradients | [CampusX -- Vanishing gradient](https://www.youtube.com/watch?v=qO_NLVjD6zE) | Why do deep sigmoid networks suffer from vanishing gradients? What does a gradient near 0 do to learning in that layer? |

> **Mini Assignment 3.2 -- Implement a 2-layer neural network from scratch:** Using only NumPy: (1) Initialize weights with He initialization. (2) Implement forward pass with ReLU hidden layer and sigmoid output. (3) Implement backprop with chain rule. (4) Train on XOR problem (it's not linearly separable -- a single layer cannot solve it). (5) Add dropout to the hidden layer. Does it help?

| # | Concept | Video | Quick quiz |
|---|---------|-------|-----------|
| 3.9 | Perceptron: the original single-neuron model | [CampusX -- Perceptron](https://www.youtube.com/watch?v=jEoW6OBElJA) | What can a single perceptron NOT learn? Why? What did this limitation cause historically? |
| 3.10 | Early stopping and learning rate scheduling | [CampusX -- Early stopping](https://www.youtube.com/watch?v=nxOp-3s2z2g) | How does early stopping prevent overfitting without changing the model? What metric do you monitor? |

---

## Section 2 -- PyTorch

| # | Concept | Video | Quick quiz |
|---|---------|-------|-----------|
| 3.11 | Tensors, autograd, computation graphs | [Patrick Loeber -- PyTorch beginner crash course](https://www.youtube.com/playlist?list=PLqnslRFeH2UrcDBWF5mfPGpqQDSta6VK4) | What does `requires_grad=True` do? What does `loss.backward()` compute? What does `.detach()` do? |
| 3.12 | nn.Module, Sequential, custom layers | [Patrick Loeber -- PyTorch nn.Module](https://www.youtube.com/playlist?list=PLqnslRFeH2UrcDBWF5mfPGpqQDSta6VK4) | What must every custom `nn.Module` implement? What does `model.parameters()` return? |
| 3.13 | Dataset, DataLoader, data pipelines | [Patrick Loeber -- PyTorch DataLoader](https://www.youtube.com/playlist?list=PLqnslRFeH2UrcDBWF5mfPGpqQDSta6VK4) | What does `shuffle=True` do in a DataLoader? Why is shuffling important for training but not evaluation? |
| 3.14 | Full training loop: zero_grad, forward, loss, backward, step | [Andrej Karpathy -- micrograd](https://www.youtube.com/watch?v=VMj-3S1tku0) | Why do you call `optimizer.zero_grad()` before each backward pass? What happens if you forget? |

> **Mini Assignment 3.3 -- Full PyTorch training loop:** Build a complete PyTorch MLP for classification on MNIST: (1) Custom Dataset class, (2) DataLoader with batch size 64, (3) 3-layer MLP with ReLU and BatchNorm, (4) training loop with Adam optimizer, (5) validation accuracy per epoch, (6) plot training and validation loss curves, (7) compute confusion matrix on test set. Target: >97% test accuracy.

| # | Concept | Video | Quick quiz |
|---|---------|-------|-----------|
| 3.15 | Transfer learning and fine-tuning pretrained models | [Andrej Karpathy -- transfer learning](https://www.youtube.com/watch?v=yofjFQddwHE) | What layers do you freeze during fine-tuning? Why? What is the difference between feature extraction and full fine-tuning? |
| 3.16 | Mixed precision training: FP16 and BF16 | [PyTorch -- Mixed precision guide](https://pytorch.org/tutorials/recipes/recipes/amp_recipe.html) | Why does FP16 training use less memory? What problem can it cause and how does GradScaler fix it? |
| 3.17 | Experiment tracking: wandb and TensorBoard | [Weights and Biases -- tutorials](https://www.youtube.com/c/weightsandbiases) | What metrics should you always log during training? Why is experiment tracking critical when you run 50+ experiments? |

---

## Section 3 -- Convolutional Neural Networks

| # | Concept | Video | Quick quiz |
|---|---------|-------|-----------|
| 3.18 | Convolutions: filters, feature maps, receptive field | [Brandon Rohrer -- How CNNs work](https://www.youtube.com/watch?v=pj9-rr1wDhM) | What does a 3x3 filter with stride 1 and padding 1 do to a 28x28 image? What is the output size? |
| 3.19 | Pooling, stride, padding | [Andrew Ng -- CNNs free YouTube](https://www.youtube.com/playlist?list=PLkDaE6sCZn6Ec-XTbcX1uRg2_u4xOEky0) | What does max pooling 2x2 with stride 2 do to a 28x28 feature map? Why is pooling used? |
| 3.20 | ResNet: skip connections and why they work | [Andrew Ng -- Classic CNN architectures](https://www.youtube.com/watch?v=dZVkygnKh1M) | What problem do skip connections solve? Why can you train a 152-layer ResNet but not a 152-layer VGG? |
| 3.21 | U-Net for segmentation | [DeepLearning.AI -- U-Net explained](https://www.youtube.com/watch?v=NhdzGfB1q74) | What is the key architectural difference between U-Net and a standard CNN? What do the skip connections in U-Net do? |

> **Mini Assignment 3.4 -- Train a CNN on CIFAR-10:** (1) Build a CNN in PyTorch with 3 conv layers + BatchNorm + ReLU + MaxPool. (2) Train for 30 epochs with Adam. (3) Add data augmentation (RandomHorizontalFlip, RandomCrop). (4) Try adding a ResNet-style skip connection. Does it improve accuracy? (5) Visualize the learned filters of the first layer. What do they detect?

---

## Section 4 -- Transformers and attention

| # | Concept | Video | Quick quiz |
|---|---------|-------|-----------|
| 3.22 | Tokens and tokenization: BPE, WordPiece | [Andrej Karpathy -- tokenization from scratch](https://www.youtube.com/watch?v=zduSFxRajkE) | What is a token? Why does GPT-4 use ~100k tokens instead of individual characters? What is a byte-pair encoding merge? |
| 3.23 | Attention mechanism: Q, K, V | [Andrej Karpathy -- attention from scratch](https://www.youtube.com/watch?v=PSs6nxngL6k) | Write the attention formula: Attention(Q,K,V) = ? What does scaling by √d_k prevent? |
| 3.24 | Self-attention and multi-head attention | [3Blue1Brown -- Attention in transformers](https://www.youtube.com/watch?v=wjZofJX0v4M) | What is the difference between self-attention and cross-attention? What does each "head" in multi-head attention learn? |
| 3.25 | Positional encoding: sinusoidal and learned | [Andrej Karpathy -- GPT from scratch](https://www.youtube.com/watch?v=kCc8FmEb1nY) | Why does the transformer need positional encoding? Self-attention alone has no sense of __? |

> **Mini Assignment 3.5 -- Implement self-attention from scratch:** Following Karpathy's GPT tutorial: (1) Implement the scaled dot-product attention in PyTorch (30 lines). (2) Implement multi-head attention. (3) Implement a full transformer block with LayerNorm, FFN, and residual connections. (4) Train a character-level language model on Shakespeare's sonnets. This is the most important DL implementation exercise in the course.

| # | Concept | Video | Quick quiz |
|---|---------|-------|-----------|
| 3.26 | Full transformer architecture: encoder, decoder | [Andrej Karpathy -- GPT from scratch](https://www.youtube.com/watch?v=kCc8FmEb1nY) | What is the difference between an encoder-only (BERT), decoder-only (GPT), and encoder-decoder (T5) transformer? |
| 3.27 | BERT: bidirectional masked language modeling | [Yannic Kilcher -- BERT paper](https://www.youtube.com/watch?v=-9evrZnBorM) | What is the masked language modeling objective? Why is BERT bidirectional but GPT is not? |
| 3.28 | Vision Transformer (ViT): patches as tokens | [Yannic Kilcher -- ViT paper](https://www.youtube.com/watch?v=TrdevFK_am4) | How does ViT turn an image into tokens? What is a patch? How does it compare to CNNs for small datasets? |

---

## Section 5 -- Generative models

| # | Concept | Video | Quick quiz |
|---|---------|-------|-----------|
| 3.29 | Autoencoders: encoder, bottleneck, decoder | [Arxiv Insights -- Autoencoders](https://www.youtube.com/watch?v=7mRfwaGGAPg) | What does the bottleneck layer force the model to learn? What is reconstruction loss? |
| 3.30 | VAE: latent space + reparameterization trick | [Arxiv Insights -- VAE explained](https://www.youtube.com/watch?v=9zKuYvjFFS8) | What is the reparameterization trick and why is it needed for backpropagation? What are the two terms in the VAE loss (ELBO)? |
| 3.31 | GAN: generator vs discriminator | [Yannic Kilcher -- GAN paper](https://www.youtube.com/watch?v=eyxmSmjmNS0) | What does the generator minimize? What does the discriminator maximize? Why can training be unstable? |
| 3.32 | Diffusion models: forward noise and reverse denoising | [Yannic Kilcher -- Diffusion models](https://www.youtube.com/watch?v=fbLgFrlTnGU) | What does the forward process do? What does the model learn in the reverse process? Why are diffusion models better than GANs for diversity? |

> **Mini Assignment 3.6 -- Train a VAE:** (1) Build a VAE in PyTorch for MNIST. (2) Implement the ELBO loss (reconstruction + KL divergence). (3) After training, visualize the 2D latent space -- color points by digit class. (4) Sample random points from the latent space and decode them. (5) Interpolate between two digits in latent space. What do you observe?

| # | Concept | Video | Quick quiz |
|---|---------|-------|-----------|
| 3.33 | Diffusion Policy for robot learning | [HuggingFace Robotics Course](https://huggingface.co/learn/robotics-course) | Why is diffusion better than behavior cloning for multimodal action distributions? What does "multimodal" mean in this context? |
| 3.34 | Self-supervised learning: SimCLR, DINO, CLIP | [Yannic Kilcher -- SimCLR explained](https://www.youtube.com/watch?v=APki8LmdJwY) | What is a "positive pair" in contrastive learning? What does SimCLR learn without any labels? |

---

## Section 6 -- LLM fine-tuning and efficiency

| # | Concept | Video | Quick quiz |
|---|---------|-------|-----------|
| 3.35 | LoRA and QLoRA: low-rank fine-tuning | [Yannic Kilcher -- LoRA explained](https://www.youtube.com/watch?v=dA-NhCtrrVE) | What does LoRA add to a pretrained weight matrix? Why does this reduce trainable parameters by 10,000x? |
| 3.36 | Quantization: INT8 and INT4 | [HuggingFace -- quantization guide](https://huggingface.co/docs/transformers/quantization) | What is the tradeoff of quantizing a model from FP32 to INT8? What does 4-bit quantization allow you to do on consumer hardware? |
| 3.37 | Knowledge distillation: teacher-student | [Two Minute Papers -- knowledge distillation](https://www.youtube.com/watch?v=lMepFKPMk3U) | What are "soft labels" and why do they carry more information than one-hot labels? |
| 3.38 | Interpretability: SHAP, LIME, GradCAM | [StatQuest -- SHAP explained](https://www.youtube.com/watch?v=VB9uV-x0gtg) | What does a SHAP value tell you about a feature? What does GradCAM visualize in a CNN? |

> **Mini Assignment 3.7 -- Fine-tune a pretrained model:** Using HuggingFace: (1) Load a pretrained DistilBERT model. (2) Fine-tune it on SST-2 sentiment analysis using LoRA (PEFT library). (3) Compare accuracy and training time vs full fine-tuning. (4) Visualize attention weights for a sample sentence. (5) Apply SHAP to explain predictions on 5 test examples.

---

## Section 7 -- JAX

| # | Concept | Video | Quick quiz |
|---|---------|-------|-----------|
| 3.39 | JAX basics: arrays, jit, grad, vmap | [Google DeepMind -- JAX tutorial](https://www.youtube.com/watch?v=juo5G3t1xAo) | What does `jax.jit` do? What does `jax.grad(f)(x)` return? What does `jax.vmap` do that a for loop doesn't? |
| 3.40 | JAX for RL: PureJaxRL and Gymnax | [PureJaxRL -- end to end JAX RL](https://github.com/luchris429/purejaxrl) | Why is JAX faster than PyTorch for RL training? What does running an entire RL environment in JAX enable? |

> **Mini Assignment 3.8 -- Implement gradient descent in JAX:** (1) Define a loss function in JAX. (2) Use `jax.grad` to compute its gradient. (3) Write a training loop using `jax.jit` for speed. (4) Compare speed vs PyTorch equivalent. (5) Use `jax.vmap` to run 100 training runs in parallel. JAX's functional style forces you to think about computation differently.
