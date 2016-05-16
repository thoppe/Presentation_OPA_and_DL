# Deep Learning
[ICLR 2016](http://www.iclr.cc/doku.php) (International Conference on Learning Representations) 
----------
Deep Learning: What's hot, what's hype and what can we use?
====*

## What is deep learning?
_and what is it not?_
    
DL is a _subset_ of machine learning.
DL is not a SVM, random forest, single layer HMM, ...
DL is defined by *multiple stacks* of layers (deep)
!(images/DLex1.png) <<height:200px;transparent>>
!(images/DLex2.png) <<height:200px;transparent>>
!(images/DLex3.png) <<transparent>> [inception model](http://arxiv.org/abs/1409.4842)
  
====

## Why so hot?
    
DL is exploding in terms of publications and use-cases.

It works ... image recognition, captioning, robotic control, text synthesis, language generation, audio encoding, ...

*Major* investment by Google, Facebook, Twitter, Intel, Baidu, Amazon, Adobe, Oracle, IBM Watson, ...
    
====*
    
## Why now?

### Datasets

### Hardware: GPU (nVidia)
!(images/nvidia-graphics-card-med.jpg) <<transparent;height:300px>>

=====*
    
### Where does deep learning fit
### into portfolio analysis?
Overlap of Natural Language Processing & Deep Learning...

#### Interpreting human language:    
tokenization, POS tagging, NE recognition, dependency parsing, ...

#### Learned representations
word (word2vec), sentence, paraphrase, document, ...

#### Applied deep learning
supervised tasks, clustering, similarity tests, document summarization, annotating / attention mechanisms, discovery, and outlier detection.

    
====*

### International Conference
### on Learning Representations
San Juan, Puerto Rico, 2016

#### Yoshua Bengio
U. Montreal, CS (22,000 citations)
    
#### Yann Lecun
Facebook, AI Director (developed CovNets, major OCR work)
!(http://www.iro.umontreal.ca/~bengioy/yoshua_en/index_files/idlarge.jpg) <<height:200px>>
!(http://yann.lecun.com/ex/images/ylc-thumb.jpeg) <<height:200px>>
    
=====


## Common patterns
It's all about the architecture!

### *MLP*: Multilayer Perceptron
### *RNN*: Recurrent Neural Networks
### *CNN*: Convolutional Neural Network
### *VAE*: Varational AutoEncoders
### *GAE*: Generative Adversarial Networks

====*
    
### *MLP*: Multilayer Perceptron
Basic idea of most neural networks
Key points: Activation functions, Layers, Backpropagation,

!(https://camo.githubusercontent.com/6cbf32d6b071f11cda62a15c7697f1381bf03789/687474703a2f2f7777772e636f646570726f6a6563742e636f6d2f4b422f646f746e65742f707265646963746f722f6e6574776f726b2e6a7067)

## Activation: $f(\mathbf{W}x + b)$
    
====*

### *RNN*: Recurrent Neural Networks
Network maintains some sense of "state"

!(http://karpathy.github.io/assets/rnn/diags.jpeg)  [The Unreasonable Effectiveness of Recurrent Neural Networks](http://karpathy.github.io/2015/05/21/rnn-effectiveness/)
    
====*

Trained on text, RNN's can reproduce passages, punctuation and style
    PANDARUS:
    Alas, I think he shall be come approached and the day
    When little srain would be attain'd into being never fed,
    And who is but a chain and subjects of his death,
    I should not sleep.
        
    Second Senator:
    They are away this miseries, produced upon my soul,
    Breaking and strongly should be buried, when I perish
    The earth and thoughts of many states.

Or titles of scientific articles (high-energy physics):
    Search for CP-Violation in Right-Handed Neutrinos
    Neutron Star Propagation as a Source of the Hadron-Hadron Scattering Measurement at the Planck Scale
    Goldstone bosons and scattering modes from two-dimensional Hamiltonians
    Baryogenesis with Yukawa Unified SUSY GUTs
    Radial scattering and dense quark matter and chiral phase transition of a pseudoscalar meson at finite baryon density
    Transition Form Factor Constant in a Quark-Diquark Model
    A New Theory of Supersymmetry Breaking
    Effective gluon propagator in QCD at zero and finite temperature and and dual gauge QCD in the BCS-BCS limit
    Light scalar pair signals in top quark multiple polarizatino

====*

### *CNN*: Convolutional Neural Network
Sparse / shared weights weights
!(images/conv_1D_nn.png) <<height:200px; transparent>>
    
!(images/mylenet.png)  <<height:200px; transparent>>
    
====*

### *CNN* + *RNN*: Image captioning
!(images/CNNRNN.png)

====*   
### *Autoencoders*
Train the network to reproduce the input
!(images/autoencoder_network1.png)

!(images/results-00.png)
!(images/results-01.png)
!(images/results-02.png)
!(images/results-03.png)
=====*
### *GAE*: Generative Adversarial Networks
Deep networks can be overtrained and brittle
Train _two_ networks, one generates, the other discriminates

!(images/adves1.png)
====*
### *GAE* + *Autoencoder*
!(images/adves2.png)

&& Unsupervised Representation Learning with Deep Convolutional Generative Adversarial Networks [arxiv:1511.06434](http://arxiv.org/abs/1511.06434)
    
=====
Not covered here
### Deep Robotic Learning
!(images/Sergey_Robots.mp4) <<height:600px>>

&& Sergey Levin, ICLR Keynote
=====*

More topics not covered (but very interesting!)
    
[BlackOut: Speeding up Recurrent Neural Network Language Models With Very Large Vocabularies](http://arxiv.org/abs/1511.06909)

[Guaranteed Non-convex Learning Algorithms through Tensor Factorization](https://arxiv.org/abs/1506.08473)

[Convergent Learning: Do different neural networks learn the same representations?](http://arxiv.org/abs/1511.07543)

[Net2Net: Accelerating Learning via Knowledge Transfer](http://arxiv.org/abs/1511.05641)

=====
## The Goldilocks Principle
[Reading Children's Books with Explicit Memory Representations] (http://arxiv.org/abs/1511.02301)

Built a corpus of children's books with attention based questions
!(images/gold.png)
Since humans need context to solve Q&A, train attention mechanisms!
=====*

### Towards Universal Paraphrastic Sentence Embeddings, [arXiv](http://arxiv.org/abs/1511.08198)
Tested sentence similarity, entailment, and sentiment classification.

An example of a positive TE (text entails hypothesis):
    text: If you help the needy, God will reward you.
    hypothesis: Giving money to a poor man has good consequences.
An example of a negative TE (text contradicts hypothesis):
    text: If you help the needy, God will reward you.
    hypothesis: Giving money to a poor man has no consequences.
An example of a non-TE (text does not entail nor contradict):
    text: If you help the needy, God will reward you.
    hypothesis: Giving money to a poor man will make you a better person.

=====*

### The Variational Fair Autoencoder, [arXiv](http://arxiv.org/abs/1511.00830)
"... learning representations that are invariant to certain nuisance or sensitive factors of variation in the data while retaining as much of the remaining information as possible. Our model is based on a variational autoencoding architecture with priors that encourage independence between sensitive and latent factors of variation."
!(images/faces.png)<<height:400px>>

=====*

### Order-Embeddings of
### Images and Language, [arXiv](http://arxiv.org/abs/1511.06361)
" Hypernymy, textual entailment, and image captioning can be seen as special cases of a single visual-semantic hierarchy over words, sentences, and images. In this paper we advocate for explicitly modeling the partial order structure of this hierarchy..."
        
!(images/orderembed1.png)<<height:400px>>
!(images/orderembed2.png)<<height:400px>>

=====*

### Multi-layer Representation Learning
### for Medical Concepts, [arXiv](http://arxiv.org/abs/1602.05568)
    
In Electronic Health Records the visit sequences of patients have multiple concepts (diagnosis, procedure, and medication codes) per visit.  This structure provides two types of relational information, namely sequential order of visits and co-occurrence of the codes within each visit. Med2Vec learns distributed representations for both medical codes and visits from a large EHR dataset with over 3 million visits, and allows us to interpret the learned representations confirmed positively by clinical experts.

=====

Thank you