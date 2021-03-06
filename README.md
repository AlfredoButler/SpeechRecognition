

## Overview

Project status: Currently designing architecture for speech to text transcription. 

---

# Lit Speech Notes

author: Unique Divine  

Core questions:
- What is the encoder-decoder model?
- What are beam search and greedy search?
- What language models and approaches will help improve speech recognition accuracy the most?

## Encoder-decoder model

- **encoder**: A model that represents sequences as vectors. Each sequence is encoded into a vector representation.  
- **decoder**: A model that takes in encoded inputs and uses them to generate the output sequences. Usually a recurrent neural network.

Both the encoder and decoder are trained simultaneously, and the trained encoder can be used to compute a distributed representation of any sequence. 

## Seq2seq (2014)

Seq2Seq, or Sequence To Sequence, is a model used in sequence prediction tasks, such as language modeling and machine translation. 
1. One LSTM is used as an encoder to read each input sequence one timestep at a time, obtaining a fixed dimensional vector representation (called a context vector)
2. Another LSTM is used as the decoder to extract the output sequence from the context vector. This decoder is conditioned on the input sequence. 
 
Seq2seq is an application of the encoder-decoder model. 

## Greedy decoder

A greedy decoder works, but it isn't the most accurate. 
- **"greedy" transition-based parsing**: A type of parsing where the parser tries to make the best decision at each configuration. This can lead to search errors when an early decision locks the parser into a poor derivation. 
- **greedy search decoder**: A decoder in which the generation of some output sequence is a result of selecting the most likely prediction at each step. 
> "[The Greedy search decoder] approach has the benefit that it is fast, but the quality of the final output sequences may be far from optimal." - Brownlee

## Beam Search

To explain beam search, we'll consider an example. Suppose we have the use the sequence to sequence use case.

## Connectionist Temporal Classification (CTC)


In speech recognition, an acoustic signal is converted into words or sub-word untis. We have a training dataset of audio clips with corresponding transcripts. Unfortunately, we face the difficult problem of figuring out a consistent way to align the characters in the transcript with the audio.

As RNNs are powerful sequence learners, they would see to be suited to perform speech recognition tasks, however RNNs require pre-segmented training data and post-processing to transform outputs into label sequences, which limits their applicability. Connectionist temporal classification (CTC) is a method for training RNNs to label unsegmented sequences. CTC helps solve the problem of not knowing the alignment between the input and output sequences. 

TODOs:
- [x] Read CTC paper (Graves, 2006) [[link]](https://wwow.cs.toronto.edu/~graves/icml_2006.pdf)
- [ ] Read CTC paper (Hannun, 2017) [[link]](https://distill.pub/2017/ctc/)
- [ ] Explain CTC algo.
  - [ ] definition
  - [x] utility
- [ ] Explain CTC loss 
  - [ ] definition
  - [ ] utility
- [ ] Explain why it's useful. 
- [ ] Use [this decoder](https://github.com/parlance/ctcdecode) to get a minimum viable product
- [ ] Describe implementation. 

### CTC Algorithm 


### CTC Loss

[wikipedia definition](https://en.wikipedia.org/wiki/Connectionist_temporal_classification)

[Pytorch CTC Loss](https://pytorch.org/docs/stable/generated/torch.nn.CTCLoss.html)

## Implementation 

Use [ctcdecode](https://github.com/parlance/ctcdecode).


---

# References 

- Sequence to Sequence Learning with NNs [[article]](https://paperswithcode.com/method/seq2seq) [[paper]](https://arxiv.org/pdf/1409.3215v3.pdf)
- Khandelwal, R. (2020). *An intuitive explanation of Beam Search*. [[article]](https://towardsdatascience.com/an-intuitive-explanation-of-beam-search-9b1d744e7a0f)
- Brownlee, J. (2020). *How to Implement a Beam Search Decoder for Natural Language Processing*. [[article]](https://machinelearningmastery.com/beam-search-decoder-natural-language-processing/)
- Hannun, A. (2017). *Sequence modeling with CTC*. Distill, 2(11), e8. [[paper]](https://distill.pub/2017/ctc/)
- A. Graves et al. (2006). *Connectionist Temporal Classification: Labelling Unsegmented Sequence Data with Recurrent Neural Networks* [[paper]](https://www.cs.toronto.edu/~graves/icml_2006.pdf)






