# `word2vec`
## and other text-mining insights
----------
### [Travis Hoppe](http://thoppe.github.io/)
NIH/NIDDK/LCP postdoc detailing at NIH/OD/DPCPSI/OPA

====*
### Who?
Background & experience.

### Why?
OPA's motivation and my interest.

### What?
Deliverables and research report.

### When?
Timeline for future projects.

====
# Background & Experience
## Research
PhD. Physics, two NIH postdocs
Allen Minton (Macromolecular crowding)
Robert Best (Computational biology, Bioinformatics)

## Extra Curricular
Organizer: [Hack and Tell DC](http://www.meetup.com/DC-Hack-and-Tell/) (900+ members)
Presenter: [Data Wranglers DC](http://www.meetup.com/Data-Wranglers-DC/)*, [Data Science DC](http://www.meetup.com/Data-Science-DC/)
Machine learning enthusiast: [Meet The Man Who Gamed Reddit With A Bot](http://www.buzzfeed.com/hamzashaban/today-ai-learned)

&& *Presenting tonight: [Black Hat Data Wrangling](http://www.meetup.com/Data-Wranglers-DC/events/225710555/)

====
# Motivation

### OPA's mission:
... enhance the impact of NIH-supported research by enabling NIH research administrators and decision makers to *evaluate and prioritize current, as well as emerging, areas of research* that will advance knowledge and improve human health.

### My focus:
Enhance current pipeline of text-processing, experiment with 
state-of-the-art tools, and showcase them on current datasets.

====*
## Primary Aims

#### *Quantify* the predictability of an observable
ex. predict (IC/MeSH/race) from grant text.

#### Automatically *build* portfolio collections
ex. cluster grants, and give high-level descriptions.

#### *Predict* scientific trends
ex. estimate current areas of growth from recently published articles.

====

## Why is this a hard problem?

Natural language is *sparse*.

OPA's current solution is TF-IDF (term frequency inverse-
document frequency). Words are represented as one-hot vectors
 and documents are summarized by the average TF-IDF + local association.

Need a *dense* embedding. Exploit words that are related to each other!

Cluster the words in an intermediate dimension, 
and work in reduced space.

====*

# Deliverables 
developed & implemented

Full text pipeline with two key features:

##    phrasal detection
##    word2vec embedding

word2vec pipeline is open sourced at [https://github.com/NIHOPA/pipeline_word2vec](https://github.com/NIHOPA/pipeline_word2vec)

====
## Text Pipeline
dataset: R01 grants

Pre-processing:
#### Identify abbreviated phrases
#### Replace phrases with token
#### Remove parenthesis
#### Transform symbols
#### Decaps text
#### POS tokenization

====*
## Identify abbreviated phrases
<div style="font-size:.8em;"> *Inflammatory Bowel Disease* (IBD) is a common and devastating immune-mediated disease in which the mucosal _immune system_ abnormally recognizes the intestinal bacterial flora leading to _chronic inflammation_. </div>

## Replace phrases with token
<div style="font-size:.8em;"> `PHRASE_inflammatory_bowel_disease` is a common and devastating immune-mediated disease in which the mucosal `PHRASE_immune_system` abnormally recognizes the intestinal bacterial flora leading to `PHRASE_chronic_inflammation` . </div>

## parts-of-speech removal
<div style="font-size:.8em;"> `PHRASE_inflammatory_bowel_disease` immune-mediated disease mucosal `PHRASE_immune_system` intestinal bacterial flora `PHRASE_chronic_inflammation` </div>
=====

## Term frequencies

!(images/token_freq2.png) <<transparent;height:430px>> Without POS removal
!(images/token_freq1.png) <<transparent;height:430px>> With POS removal (note absolute scale)

Part of speech removal elegantly removes
"stop-words" and extraneous verbosity.

====

# `word2vec`
deep learning embedding developed an engineer at Google$.^1$
## $\arg \max_{\theta} \Pi_{(w,c)\in D} \ p(c | w;\theta)$

Optimize the parameters $\Theta$ by maximizing the conditional probability of a given context $c$ given a word $w$ over all sets of pairs $(w,c) \in D$.

Goal is to predict the most likely word given the surrounding words.
I ate the *cows* at the orchard yesterday.
I ate the *apple* at the orchard yesterday.
I ate the *NIH* at the orchard yesterday.

&& $(1)$ [Efficient Estimation of Word Representations in Vector Space](http://arxiv.org/abs/1301.3781), Mikolov, (2013)
====*
# `word2vec`

Once trained, produces a "dense" d-dimensional vector for each word on a unit hypersphere. `word2vec` $d \approx 200$; `TF-IDF` $d \approx 10000$.

Words close to each other in the space are also semantically related.

Combined with phrasal detection from abbreviations, this leads to natural descriptions of scientific terms when applied to grant data.

====

### Nearby words identified by cosine similarity
What is related to the concept of the "central nervous system"?
====+
    PHRASE_central_nervous_system
      0.7556 CN                  
      0.6131 demyelination       
      0.6098 PHRASE_multiple_sclerosis
      0.6025 demyelinating       
      0.5722 blood-brain         
      0.5621 microglium          
      0.5602 neuropathogenesi    
      0.5575 neurological        
      0.5556 glial               
      0.5515 neuroinflammation   

     PHRASE_magnetic_resonance_imaging
      0.6074 PHRASE_magnetic_resonance
      0.5438 image               
      0.5121 T1-weighted         
      0.5084 MRus                
      0.5004 PHRASE_diffusion_tensor
      0.4904 multimodal          
      0.4896 contrast-enhanced   
      0.4860 non-invasive        
      0.4838 PHRASE_computed_tomography
      0.4757 MR                  

====*
### Nearby words identified by cosine similarity
Also works for enzymes, proteins and organisms!

     GTPase
      0.8572 Rho                 
      0.8260 guanine_nucleotide_exchange
      0.8203 guanine_nucleotide_exchange_factors
      0.8028 GEF                 
      0.7805 Rac                 
      0.7760 Cdc42               
      0.7696 GTP-bound           
      0.7650 GTP-binding 

     Saccharomyce
      0.8939 cerevisia           
      0.8558 yeast               
      0.7432 baker               
      0.7395 eukaryote           
      0.6669 Kluyveromyce        
      0.6499 pombe               
      0.6479 eukaryotic          
      0.6033 S.cerevisia         

====*
### Topic disambiguation, what is "activity"?
====+
    activity
      0.6707 inhibition          
      0.6360 role                
      0.5930 activation          
      0.5861 pathway             
     PHRASE_physical_activity
      0.7892 PHRASE_sedentary_behavior
      0.7609 sedentary           
      0.7400 PHRASE_healthy_eating
      0.7263 overweight          
     PHRASE_sympathetic_nerve_activity
      0.7476 baroreflex          
      0.7445 sympathetic         
      0.7411 sympathoexcitation  
      0.7300 PHRASE_renal_sympathetic_nerve_activity
...
	 PHRASE_spontaneous_activity
     PHRASE_epileptiform_activity
     PHRASE_structure_activity_relationship
     PHRASE_high_activity
     PHRASE_slow_wave_activity
     PHRASE_structure_activity_relationships
     PHRASE_spontaneous_brain_activity
     PHRASE_triggered_activity
     PHRASE_constitutive_activity
     PHRASE_low_activity

====*

# Word analogies
The _geometry_ of the embedding can reveal word relations 
beyond simple distance measures: $b_2 \approx b_1 + (a_2 - a_1)$
====+

<br>
### malaria : mosquito <span style="text-transform:lowercase;font-weight:normal">as</span> Lyme : *tick*

### protein : fold <span style="text-transform:lowercase;font-weight:normal">as</span> RNA : *base-pairing*

### sodium : Na <span style="text-transform:lowercase;font-weight:normal">as</span> potassium : *K*

====

## Document scoring 
A document can be summarized by the norm-sum its individual words. 

Similar documents can be found in this new projection.

#### Species richness and resilience in gut microbial communities
    The role of a core microbiota network in recovering from community perturbations
    Diversity, productivity and resilience in chemostat models of oral communities
    Genes, Pathways and Resource Allocation: Modeling Intestinal Communities
    Mapping and predicting metabolic fluxes between the ileal microbiome and host
    Evolvement of the Oral Microbiome from Birth to Infancy
    Open symbiosis in social insects: Acquisition and dynamics of defense mutualist c
    The Phylosymbiotic Signal of Host-Associated Microbiomes
    Proteogenomic analysis of inflammation and dysbiosis in the infant gut
    The pig as a model of the human gastrointestinal microbiome

====*

## Document scoring 
Semantics are preserved across sections.

!(images/cos_sim_abstract_vs_aims.png) <<transparent; height:600px>>

====*

## Class prediction
Try to predict an observable from only R01 abstract text.
Build a random-forest classifier from document embeddings.

Validates that the embedding is robust.
Helps determine what information could be found by clustering.

    class name        | minimal prediction   | best prediction
    ------------------------------------------------------------------
    top 10 IC           0.1441                 0.8338
    animalSubjectsCode  0.5138                 0.8920
    humanSubjectsCode   0.6309                 0.8764
    median funding      0.5001                 0.6927
    discussed           0.5323                 0.6239


%!(images/confusion_matrix.png)<<transparent>>

====
  
## Document clustering
#### (ongoing project, projected time: 1 month)

Unsupervised learning is hard!
What is a good cluster when you don't know the categories?
  
Perform experiments on PLoS and ZIA data.

PLoS tracks subject areas in multiple "tiers".
ZIA are scored as internal grants.

====*
## Clustering metrics
Use assigned categories from PLoS to score a given cluster.
Over 17,000 categories, organized by taxonomy. [Full list](PLoS_cat.txt)

PLoS category sample
    Biology and life sciences      
     Anatomy     
      Abdomen    
       Peritoneum   
        Mesentery  
      Biological tissue    
       Adipose tissue   
        Brown adipose tissue  
       Connective tissue   
        Bone  
         Bone density 
         Bone matrix 
         Diaphyses 
         Epiphyses 
         Growth plate 
         Osteoclasts 
  
====

## Predicting scientific trends
#### (future work, projected time: 6 months - 1 year)
Instead of looking at rising keywords, we can look at areas in the dense embedding that have momentum. This will track growth around "semantics" and can be validated from historical data.

!(images/DPM_image2.png) <<transparent; height:400px>>
!(images/DPM_image1.png) <<transparent; height:400px>>

&& [A Dirichlet Process Mixture Model for Spherical Data](http://jmlr.org/proceedings/papers/v38/straub15.html), _Straub et. al._ (2015)

====

# Thank you.

