# Phase 03C -- NLP and Language Models

> **Time estimate:** 3-4 weeks  
> **Rule:** Every concept has a Quick Quiz. Every 3-4 concepts has a Mini Assignment.

---

## Section 1 -- Classical NLP

| # | Concept | Video | Quick quiz |
|---|---------|-------|-----------|
| NLP.1 | Bag of words and TF-IDF | [StatQuest -- Bag of words and TF-IDF](https://www.youtube.com/watch?v=OGK9SHt8SWg) | What does TF-IDF penalize that raw word count doesn't? Why is "the" a bad feature but "robot" is a good one? |
| NLP.2 | Tokenization: BPE, WordPiece, SentencePiece | [Andrej Karpathy -- tokenization from scratch](https://www.youtube.com/watch?v=zduSFxRajkE) | What is a merge in BPE tokenization? Why does "unhappiness" become fewer tokens than you might expect? |
| NLP.3 | Word embeddings: Word2Vec, GloVe, FastText | [StatQuest -- Word Embeddings](https://www.youtube.com/watch?v=viZrOnJclY0) | What does it mean for word vectors to encode semantic similarity? How does `king - man + woman ≈ queen` work mathematically? |
| NLP.4 | Text preprocessing: stemming, lemmatization, stopwords | [freeCodeCamp -- NLP with Python full course](https://www.youtube.com/watch?v=X2vAabgKiuM) | What is the difference between stemming and lemmatization? Give an example where they give different results. |

> **Mini Assignment NLP.1 -- Text classification without transformers:** (1) Load the 20 Newsgroups dataset. (2) Build a TF-IDF feature matrix. (3) Train a Logistic Regression classifier. (4) Report accuracy and F1 per class. (5) Visualize the most important TF-IDF features for 3 different classes. (6) Compare with a Naive Bayes classifier on the same features. This baseline is often surprisingly hard to beat with more complex models.

| # | Concept | Video | Quick quiz |
|---|---------|-------|-----------|
| NLP.5 | RNN and LSTM for sequence modeling | [Stanford CS224N -- Lecture 5](https://www.youtube.com/playlist?list=PLoROMvodv4rMFqRtEuo6SGjY4XbRIVx76) | Why does an RNN struggle with long sequences? What gates in an LSTM prevent vanishing gradients? |
| NLP.6 | Seq2seq and attention for translation | [Stanford CS224N -- Lecture 8](https://www.youtube.com/playlist?list=PLoROMvodv4rMFqRtEuo6SGjY4XbRIVx76) | What is the bottleneck problem in vanilla seq2seq? How does attention resolve it? |

---

## Section 2 -- Transformer-based NLP

| # | Concept | Video | Quick quiz |
|---|---------|-------|-----------|
| NLP.7 | BERT: masked language modeling and fine-tuning | [Yannic Kilcher -- BERT paper explained](https://www.youtube.com/watch?v=-9evrZnBorM) | What percentage of tokens does BERT mask during training? What are the two pretraining objectives of the original BERT? |
| NLP.8 | Fine-tuning BERT for classification and NER | [HuggingFace -- NLP Course](https://huggingface.co/learn/nlp-course) | What layer do you add on top of BERT for sentence classification vs token classification (NER)? |
| NLP.9 | Sentence-BERT: semantic sentence embeddings | [HuggingFace -- Sentence Transformers](https://www.sbert.net/docs/training/overview.html) | What training objective makes Sentence-BERT embeddings suitable for semantic similarity? What is a siamese network structure? |
| NLP.10 | GPT: autoregressive language modeling | [Andrej Karpathy -- GPT from scratch](https://www.youtube.com/watch?v=kCc8FmEb1nY) | What is the difference between BERT's bidirectional attention and GPT's causal (masked) attention? Why does GPT use causal masking? |

> **Mini Assignment NLP.2 -- Fine-tune BERT on a custom task:** (1) Choose a text classification dataset (e.g., AG News, IMDb). (2) Load `distilbert-base-uncased` from HuggingFace. (3) Fine-tune for 3 epochs using the Trainer API. (4) Report accuracy, F1, and confusion matrix. (5) Compare with TF-IDF + Logistic Regression from Mini Assignment NLP.1. How much does BERT improve over TF-IDF?

---

## Section 3 -- Large Language Models

| # | Concept | Video | Quick quiz |
|---|---------|-------|-----------|
| NLP.11 | Instruction tuning: InstructGPT and FLAN | [Yannic Kilcher -- InstructGPT explained](https://www.youtube.com/watch?v=TqOeMYtOc1w) | What is the difference between a base LLM and an instruction-tuned LLM? What data format does instruction tuning use? |
| NLP.12 | RLHF: reinforcement learning from human feedback | [Yannic Kilcher -- RLHF and InstructGPT](https://www.youtube.com/watch?v=TqOeMYtOc1w) | What are the 3 stages of RLHF? What does the reward model predict? Why is PPO used in stage 3? |
| NLP.13 | Open-source LLMs: LLaMA, Mistral, Gemma | [Two Minute Papers -- LLaMA overview](https://www.youtube.com/watch?v=E5OnoYF2oAk) | What architectural improvements does Mistral use over the original LLaMA? What is grouped query attention? |
| NLP.14 | LoRA and QLoRA: efficient fine-tuning | [Yannic Kilcher -- LoRA explained](https://www.youtube.com/watch?v=dA-NhCtrrVE) | What does LoRA add to a weight matrix W? Write the LoRA formula. Why does this reduce trainable parameters by 10,000x? |

> **Mini Assignment NLP.3 -- Fine-tune LLaMA with LoRA:** (1) Using HuggingFace PEFT library, load LLaMA-3.2-1B. (2) Apply LoRA (r=8, alpha=16) to the attention layers. (3) Fine-tune on a custom instruction dataset (500 examples minimum). (4) Compare outputs before and after fine-tuning. (5) Measure GPU memory usage with LoRA vs full fine-tuning (you can estimate with QLoRA in 4-bit).

| # | Concept | Video | Quick quiz |
|---|---------|-------|-----------|
| NLP.15 | RAG: retrieval-augmented generation | [LlamaIndex -- RAG from scratch](https://www.youtube.com/watch?v=TRjq7t2Ms5I) | What problem does RAG solve that fine-tuning doesn't? What are the two stages of RAG (retrieval + generation)? |
| NLP.16 | Prompt engineering: zero-shot, few-shot, CoT | [Andrej Karpathy -- prompting](https://www.youtube.com/watch?v=bZQun8Y4L2A) | What is chain-of-thought prompting? Why does asking the model to "think step by step" improve performance? |
| NLP.17 | LLM evaluation: BLEU, ROUGE, BERTScore | [Stanford CS224N -- evaluation](https://www.youtube.com/playlist?list=PLoROMvodv4rMFqRtEuo6SGjY4XbRIVx76) | What does a BLEU score of 0.4 mean? Why is BLEU a poor metric for open-ended generation? |
| NLP.18 | Speech recognition with Whisper | [OpenAI Whisper -- GitHub](https://github.com/openai/whisper) | What training data was Whisper trained on? How do you transcribe a .wav file in 3 lines of Python using the whisper library? |

> **Mini Assignment NLP.4 -- Build a RAG system:** (1) Load 10 PDF documents (use your VT lecture PDFs). (2) Chunk them and embed with a Sentence Transformer. (3) Store in a vector database (FAISS or Chroma). (4) Given a question, retrieve the top 3 relevant chunks. (5) Pass retrieved context + question to an LLM to generate an answer. (6) Test with 10 questions about your HRI course. This is production-level RAG.

---

## Section 4 -- Practical NLP tools

| # | Concept | Video | Quick quiz |
|---|---------|-------|-----------|
| NLP.19 | HuggingFace Transformers: from_pretrained, pipeline, tokenizer | [HuggingFace NLP Course](https://huggingface.co/learn/nlp-course) | What does `AutoModel.from_pretrained('bert-base-uncased')` do? What is the difference between `pipeline('sentiment-analysis')` and loading the model manually? |
| NLP.20 | HuggingFace Datasets: loading, processing, streaming | [HuggingFace NLP Course](https://huggingface.co/learn/nlp-course) | What does `dataset.map(tokenize_function, batched=True)` do? Why is streaming useful for large datasets? |
| NLP.21 | SpaCy: industrial-strength NLP | [freeCodeCamp -- NLP with Python](https://www.youtube.com/watch?v=X2vAabgKiuM) | What does `nlp = spacy.load('en_core_web_sm')` give you? What does `doc.ents` contain? |
| NLP.22 | LangChain and building LLM applications | [LangChain -- official tutorials](https://www.youtube.com/watch?v=TRjq7t2Ms5I) | What is a "chain" in LangChain? What problem does LangChain solve that using the API directly doesn't? |

> **Mini Assignment NLP.5 -- NLP for HRI:** Design and build an NLP component for a robot: (1) Use Whisper to transcribe a spoken instruction ("pick up the blue cup"). (2) Use SpaCy to extract the object name and color from the transcription. (3) Use CLIP to ground the extracted description to an actual object in an image. (4) Return the pixel location of the object. This is a complete voice-to-vision grounding pipeline that real HRI systems use.
