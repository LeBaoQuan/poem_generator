# Related research summary for Vietnamese Poem Generator Project 

1. Semantics improvement in Vietnamese Poem Generation

- this model is built on top of GPT-2
- Luc Bat poem style rules:
    - 6th word of 1st line rhyme with 6th word 2nd line
    - 8th word of 2nd line rhyme with 6th word in 3rd line & 4th line
    - 8th word of 3rd line rhyme with 6th word in 4th line & 5th line
    - so on

    - 2nd, 4th, 8th word are mang thanh bằng, 4th word mang thanh trắc

- To improve semantics, we refined the model
output in each pair of sentences generated to constraint the
context by embedding with the previous sentence

!https://github.com/LeBaoQuan/PoemGenerator/blob/main/custom_eval_modal.png

- Evaluation module:

- we must first create a dictionary that
includes all rhymes and tones connected while adhering to
some clear criteria derived from reliable sources of information.

- Using the Luc Bat principles, we can readily determine that
there are (3*n-1) words that require rhyme checking and (7*n)
words with tones in each stanza, where n is the number of
sentence pairings. So we create a scoring module in which the
rhyme rules account for 70 percentages of the overall score
of a quatrain and tone accounts for 30 percentages. And the
maximum score each stanza can reach is 100. 

!https://github.com/LeBaoQuan/PoemGenerator/blob/main/sp_gpt2_model.png

2. Language Models are Few-Shot Learners (GPT-3)
- the same model and architecture as GPT-2 [RWC+19], including the modified initialization, pre-normalization, and reversible tokenization described therein
- the exception that we use alternating dense and locally banded sparse
attention patterns in the layers of the transformer
- 
--- this one too complicated to actually understand !?!?

3. Analysis of metrics used for performance measurement in NLP 

A. RUGUE (Recall Oriented Understudy for Gisting Evaluation)
- calculating the syntactic overlap between candidate and reference text
- 
B. BLEU (Bilingual Evaluation Understudy) - mainly for translation
C. BERTScore
- captures the semantic aspect by using the contextualized embeddings generated by the BERT model.
D. METEOR (Metric for Evaluation of Translation with Explicit ORdering) - for translation
E. MWD (Word Mover's Distance)
- determine the semantic closeness between the generated and the reference text piece