# Model Selection Guide -- Which ML Model for Which Problem?

> This is the most practically important file in the entire repo. Knowing that random forests exist is not enough. You need to know WHEN to use random forests vs XGBoost vs a neural network vs logistic regression. This guide answers that question for every major problem type.

---

## The core question: what kind of problem do you have?

Before picking a model, answer these three questions:

1. **What is your output?** (number / category / cluster / generated content / sequence / ranking)
2. **How much labeled data do you have?** (<1K / 1K-100K / 100K-10M / 10M+)
3. **What matters most?** (accuracy / speed / interpretability / uncertainty / data efficiency)

---

## Section 1 -- Tabular / structured data

> Most real-world business ML runs on tabular data (spreadsheets, databases). This is where classical ML dominates.

| Problem | Best model | Why | When NOT to use it |
|---------|-----------|-----|-------------------|
| Binary classification, <100K rows | Logistic regression | Fast, interpretable, gives probabilities, easy to deploy | When data has complex nonlinear patterns |
| Binary classification, <100K rows | Random forest | Handles nonlinearity, robust to outliers, feature importance built in | When you need a probability calibration or >1M rows |
| Binary/multi-class, any size | XGBoost or LightGBM | Usually wins on tabular data benchmarks, fast, handles missing values | When you need true uncertainty estimates |
| Regression, <100K rows | Ridge or Lasso regression | Interpretable, L1 gives automatic feature selection | When relationships are highly nonlinear |
| Regression, any size | XGBoost or LightGBM | Consistently best regression performance on tabular data | When you need uncertainty bounds |
| Regression with uncertainty | Gaussian process | Full uncertainty quantification, works with small data | Does not scale to >50K rows without approximations |
| Multi-class, many classes | Softmax logistic regression | Simple, interpretable, calibrated probabilities | When classes have very unequal sizes |
| Multi-label classification | Binary classifiers per label (OvR) | Simple and works well | When labels have strong correlations |
| Anomaly detection | Isolation forest | Fast, no class labels needed, scales well | When you have labeled anomalies (use a classifier instead) |
| Anomaly detection, with labels | One-class SVM or autoencoder | Models normal distribution, detects deviations | One-class SVM does not scale to large datasets |
| Survival analysis | Cox proportional hazards, survival forests | Handles censored data correctly | When time-to-event is not the output |
| Ranking / recommendation | Gradient boosted trees + LTR | LambdaMART is standard in industry | When you have implicit feedback only (use matrix factorization) |
| Imbalanced binary classification | XGBoost + class weights + threshold tuning | Handles imbalance natively | Never ignore class imbalance -- models will predict majority class |

### The tabular data rule of thumb

```
Always try this order:
1. Logistic/linear regression baseline (2 minutes to train)
2. Random forest (5 minutes, often good enough)
3. XGBoost or LightGBM (usually the best)
4. Neural network (only if 1-3 are not good enough -- rare for pure tabular data)
```

**Neural networks are NOT better than XGBoost on tabular data in most cases.** This is one of the most important and counterintuitive facts in applied ML. Papers like "Why do tree ensembles still outperform neural networks on tabular data?" (2022) confirm this experimentally.

---

## Section 2 -- Image and vision data

| Problem | Best model | Why | When to use alternatives |
|---------|-----------|-----|------------------------|
| Image classification, small dataset (<10K images) | Pretrained ResNet/EfficientNet fine-tuned | Transfer learning requires very little data | Only train from scratch if you have 1M+ images |
| Image classification, large dataset | EfficientNet-B4 or ViT-B/16 | Best accuracy-compute tradeoff | ViT needs more data to train from scratch |
| Real-time object detection | YOLOv8 (nano or small) | Best speed/accuracy for real-time use | Use DETR if speed is not critical and you need better small object detection |
| High-accuracy object detection | DETA, DETR, Co-DETR | Transformer-based, better at small objects | Much slower than YOLO, cannot run real-time on edge devices |
| Instance segmentation | Mask R-CNN or YOLOv8-seg | Mature, well-supported, good accuracy | Use SAM if you need zero-shot segmentation on new categories |
| Semantic segmentation | DeepLab v3+, SegFormer | SegFormer: transformer-based, strong accuracy | Use simpler models (FCN) if you have limited GPU |
| Open-vocabulary segmentation | SAM (Segment Anything) | Zero-shot -- segments anything from a point or box prompt | Slower than task-specific models, no semantic labels |
| Depth estimation | DepthAnything v2, AdaBins | Monocular depth from a single image | Use stereo cameras for metric depth -- monocular depth is relative |
| Human pose estimation | RTMPose, OpenPose, ViTPose | Different accuracy/speed tradeoffs | Use RTMPose for real-time, ViTPose for best accuracy |
| Face recognition | ArcFace or AdaFace on a ResNet backbone | Industry standard, state of the art | Do not use as-is without addressing bias and privacy |
| Image generation | Stable Diffusion (SDXL or SD3) | Open source, best quality | Use DALL-E 3 API if you do not want to self-host |
| Image editing/inpainting | Stable Diffusion + ControlNet | Precise control over generation | Complex to set up |
| Medical image segmentation | U-Net | Designed for biomedical, works with very small datasets | Use newer variants (nnU-Net) for competitive performance |
| 3D scene reconstruction | NeRF, Gaussian Splatting | Photorealistic 3D from 2D images | Slow to train, not real-time |
| Video action recognition | SlowFast, Video Swin Transformer | Best accuracy on video benchmarks | Very slow inference, not real-time |

---

## Section 3 -- Text and language data

| Problem | Best model | Why | When to use alternatives |
|---------|-----------|-----|------------------------|
| Text classification, <10K samples | Fine-tuned BERT (distilbert-base) | Few samples, needs pretrained representations | Use logistic regression on TF-IDF for very simple tasks |
| Text classification, large dataset | Fine-tuned RoBERTa or DeBERTa | Best accuracy on classification benchmarks | Slower than distilBERT |
| Sentiment analysis | Fine-tuned BERT or RoBERTa | Industry standard | For simple positive/negative use a lexicon-based approach first |
| Named entity recognition (NER) | Fine-tuned BERT + token classification | Standard approach, strong results | SpaCy for production with speed requirements |
| Question answering (extractive) | Fine-tuned BERT or RoBERTa on SQuAD | Extract answer span from passage | Use RAG if you need generative answers |
| Question answering (generative) | RAG pipeline + LLM | Combines retrieval with generation | Complex to set up and maintain |
| Machine translation | MarianMT (fine-tuned), OPUS models | Open source, domain-specific | Use DeepL or Google Translate API for general translation |
| Text generation / chatbot | LLaMA 3, Mistral 7B (fine-tuned) | Best open-source models | Use GPT-4 API if quality is paramount and cost is acceptable |
| Text summarization | BART, T5, PEGASUS | Pretrained for summarization | Use extractive methods (TextRank) if you need speed |
| Semantic similarity | Sentence-BERT (all-MiniLM-L6-v2) | Fast, good quality embeddings | Use OpenAI embeddings API for best quality |
| Document search / retrieval | BM25 (baseline) + Dense retrieval (DPR) | BM25 is fast and hard to beat, DPR adds semantic matching | RAG combines both |
| Code generation | StarCoder2, CodeLlama | Open source code LLMs | Use GitHub Copilot or GPT-4 API in production |
| Speech recognition | Whisper (medium or large-v3) | Best open-source ASR by far | Use faster-whisper for 4x speed |
| Text to speech | Coqui TTS, Bark | Open source, good quality | ElevenLabs API for production quality |

### The text/NLP rule of thumb

```
Always try this order:
1. TF-IDF + Logistic Regression (5 minutes -- often surprisingly strong)
2. Fine-tune distilBERT (if you have >1K labeled examples)
3. Fine-tune RoBERTa / DeBERTa (best accuracy, more GPU)
4. Fine-tune LLaMA / Mistral with LoRA (if you need generative output)
```

---

## Section 4 -- Time series data

| Problem | Best model | Why | When to use alternatives |
|---------|-----------|-----|------------------------|
| Short-term univariate forecasting | ARIMA, ETS, Prophet | Simple, interpretable, no GPU needed | Neural nets for longer horizons or many series |
| Long-horizon univariate forecasting | N-BEATS, N-HiTS | Best accuracy on benchmark datasets | Requires more data |
| Multivariate forecasting | TFT (Temporal Fusion Transformer), PatchTST | Handles multiple related series | Complex to configure |
| Anomaly detection in time series | Isolation forest, LSTM autoencoder | Can be trained unsupervised | LSTM autoencoder needs tuning |
| Classification of time series | InceptionTime, Rocket | Best time series classification accuracy | Rocket is fastest (uses random convolutional features) |
| Many time series at once | TimesFM (Google), Chronos (Amazon) | Foundation models for time series -- zero-shot | Very new, still maturing |

---

## Section 5 -- Graph and relational data

| Problem | Best model | Why | When to use alternatives |
|---------|-----------|-----|------------------------|
| Node classification | GraphSAGE, GAT (Graph Attention Network) | Standard approaches, well-supported | GCN for simpler graphs |
| Link prediction | GraphSAGE, SEAL | Predicting missing edges | Simple heuristics (common neighbors) often work surprisingly well |
| Graph classification | GIN (Graph Isomorphism Network) | Best expressive power | GCN is faster but less expressive |
| Molecular property prediction | GNN on molecular graphs, SchNet | Chemistry-specific architectures | Use pretrained ChemBERTa for SMILES strings |
| Knowledge graph completion | TransE, RotatE, ComplEx | Embedding-based KG completion | Use GNNs if you need inductive reasoning |
| Recommendation (graph-based) | PinSage, LightGCN | Leverages user-item graph structure | Use matrix factorization if you do not have graph structure |

---

## Section 6 -- Reinforcement learning applications

| Problem | Best model | Why |
|---------|-----------|-----|
| Discrete action spaces (games, grid worlds) | DQN, Rainbow DQN | Value-based, handles discrete actions well |
| Continuous control (robot arms, locomotion) | SAC, TD3 | Off-policy, sample efficient, continuous actions |
| Safety-critical continuous control | SAC + CBF constraints, CPO | Adds safety guarantees during training |
| Sparse rewards | HER + SAC | Hindsight makes sparse rewards dense |
| Multi-agent cooperation | MADDPG, MAPPO | Multi-agent versions of DDPG and PPO |
| Offline RL (learn from fixed dataset) | IQL, CQL, TD3+BC | No environment interaction needed |
| Large discrete action spaces | PPO + action masking | Mask invalid actions for efficiency |
| Sim-to-real robot transfer | Domain randomization + SAC/PPO | Randomized physics reduces reality gap |
| Human-in-the-loop RL | RLHF, TAMER, reward learning | Incorporates human preferences as reward |

---

## Section 7 -- Audio data

| Problem | Best model | Why |
|---------|-----------|-----|
| Speech recognition | Whisper large-v3 | Best open-source ASR |
| Speaker diarization | pyannote.audio | Who spoke when |
| Keyword spotting | EfficientNet on mel spectrograms | Lightweight, runs on device |
| Music generation | MusicGen (Meta) | Open source, controllable |
| Audio classification | CNN on mel spectrograms | Fast, effective |
| Audio separation | Demucs (Meta) | Best open-source source separation |

---

## Section 8 -- Multimodal data (text + images + other)

| Problem | Best model | Why |
|---------|-----------|-----|
| Image captioning | BLIP-2, LLaVA | Image to text, strong zero-shot |
| Visual question answering | LLaVA-1.6, InternVL | Best open-source VQA models |
| Image-text matching / retrieval | CLIP | Zero-shot, works out of the box |
| Document understanding (OCR + layout) | LayoutLM, Donut | Understands document structure |
| Video + text | VideoCLIP, Video-LLaVA | Extends CLIP / LLaVA to video |
| Robot control from vision + language | RT-2, OpenVLA, Pi0 | VLA models -- the cutting edge of HRI |

---

## Section 9 -- Small data regimes (when you have very little labeled data)

This is a critical section. Most tutorials assume large datasets. In real research (especially HRI), you often have <500 labeled examples.

| Data size | What to do | Why |
|-----------|-----------|-----|
| 0 labeled examples | Zero-shot with GPT-4, CLIP, or Whisper | Foundation models generalize without fine-tuning |
| 10-50 labeled examples | Few-shot prompting, k-NN on embeddings | Do not fine-tune with this little data -- you will overfit |
| 50-500 labeled examples | Fine-tune only the last 1-2 layers of a pretrained model, use LoRA | Full fine-tuning overfits, feature extraction is safer |
| 500-5000 labeled examples | Full fine-tuning of a small pretrained model (distilBERT, ResNet-18) | Enough data for fine-tuning but choose a small model |
| 5000+ labeled examples | Full fine-tuning of any size pretrained model | Standard fine-tuning works well |
| 50K+ labeled examples | Train from scratch or fine-tune large models | At this scale you can afford full model updates |

---

## Section 10 -- The model selection decision tree

```
WHAT IS YOUR DATA TYPE?
|
|-- TABULAR (rows and columns)
|   |-- Classification --> Logistic regression -> Random forest -> XGBoost -> NN
|   |-- Regression --> Linear/Ridge -> Random forest -> XGBoost -> NN
|   |-- Clustering --> K-means -> DBSCAN -> GMM
|   |-- Anomaly detection --> Isolation forest -> Autoencoder
|
|-- IMAGES
|   |-- Classification --> Pretrained CNN (ResNet/EfficientNet) fine-tuned
|   |-- Detection --> YOLOv8 (speed) or DETR (accuracy)
|   |-- Segmentation --> YOLOv8-seg / SAM (zero-shot) / U-Net (medical)
|   |-- Generation --> Stable Diffusion
|
|-- TEXT
|   |-- Classification --> TF-IDF+LR -> fine-tuned BERT -> fine-tuned RoBERTa
|   |-- Generation --> LLaMA/Mistral fine-tuned with LoRA
|   |-- Search/Retrieval --> BM25 + DPR (RAG)
|   |-- Speech --> Whisper
|
|-- TIME SERIES
|   |-- Short-term univariate --> ARIMA / Prophet
|   |-- Long-term / multivariate --> TFT / N-BEATS
|   |-- Anomaly --> Isolation forest / LSTM autoencoder
|
|-- GRAPH
|   |-- Node classification --> GraphSAGE / GAT
|   |-- Link prediction --> SEAL / GraphSAGE
|
|-- SEQUENTIAL DECISIONS
|   |-- Discrete actions --> DQN
|   |-- Continuous actions --> SAC / TD3
|   |-- Human feedback --> RLHF / reward learning
|
|-- MULTIMODAL
|   |-- Image + text --> CLIP / LLaVA
|   |-- Robot + vision + language --> OpenVLA / RT-2
```

---

## Section 11 -- When to use classical ML vs deep learning

This is the single most important judgment call in applied ML.

| Use classical ML (XGBoost, SVM, RF) when: | Use deep learning when: |
|-------------------------------------------|------------------------|
| Data is tabular (rows and columns) | Data is images, audio, or raw text |
| You have <50K examples | You have >100K examples (or can use pretrained models) |
| You need interpretability and explanation | Black-box accuracy is acceptable |
| You need fast training and iteration | You have GPU and time |
| You need a model that runs on a CPU in production | You can afford GPU inference |
| The problem is well-defined with good features | Raw perceptual input needs feature learning |
| Debugging needs to be easy | Accuracy improvements justify complexity |

**The honest truth:** In most real business settings, a well-tuned XGBoost model beats a neural network on tabular data. Neural networks win on images, audio, text, and anything where raw perceptual features matter. When in doubt, benchmark both.

---

## Resources for learning model selection

| Resource | What it covers |
|---------|---------------|
| [scikit-learn -- algorithm cheat sheet](https://scikit-learn.org/stable/tutorial/machine_learning_map/index.html) | Official flowchart for classical model selection |
| [Papers with Code -- SOTA tables](https://paperswithcode.com) | State of the art for every benchmark -- see which models win |
| [Hands-On ML (Geron)](https://github.com/ageron/handson-ml3) | Practical model selection guidance throughout |
| Kilian Weinberger -- Cornell CS4780 lecture notes | Theoretical foundations for when each model is appropriate |
| [ML Mastery -- algorithm tours](https://machinelearningmastery.com) | Algorithm comparisons by problem type |
