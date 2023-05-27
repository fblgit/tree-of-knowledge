# tree-of-knowledge 19.05.2023
ToK aka Tree of Knowledge for Large Language Models LLM. It's a novel dataset that inspires knowledge symbolic correlation in simple input and output prompts. It can be used to efficiently drive Tree-of-Thoughts, Chain-of-Knowledge, and similar approaches.
## chain-of-knowledge 27.05.2023
...

Can these two be put together?
* Tree-of-Thoughts https://arxiv.org/pdf/2305.10601.pdf
* SYMBOL TUNING IMPROVES IN-CONTEXT LEARNING https://arxiv.org/pdf/2305.08298v1.pdf

One of the answers can be:
* Chain of Knowledge https://arxiv.org/pdf/2305.13269.pdf

*But it can be improved, efficiently using TOK as language of exchange between the steps.*

I am not an expert on this, and I do not have a laboratory or a gpu/tpu compute fleet, but I tried to make some experiments for the last few months and the results are surprising in many aspects.
**Maybe you can put it to a more strong test or scenario?**
*Please if this novel idea inspired you, cite the repo :)*

Some ideas that sounds plausible:
- A model trained with a majority of high quality TOK & Natural Language datasets can be small and strong in reasoning.
- A model trained with a mixture of high quality TOK & Natural Language datasets ca be fine-tuned further with new information
- A model trained with mostly TOK can be chained to another LLM to summarize the current context as a compacted memory
- A model trained with mostly TOK can be chained to another LLM to filter nunances by translating NL to TOK and viceversa
- A model with a Head purely based in TOK can drive the relationship of the context
- yours?

**The file data-foundation.json is the file used to fine-tune a model to being able to extract more terms**

The set experimentially can be used with multiple purposes:

* Knowledge Extraction from a Model
* Fine Tuning a model with newer data
* Create Granular Domain Knowledge Sets
* Improve training performance
* Model Head to drive TOK based context
* Chain Knowledge
* Trees of Relationship based on Symbolic Knowledge

Here are some examples in different disciplines from the original set:

```
  {
    "instruction": "Describe energy",
    "input": "",
    "output": "Energy AS ability TO do work OR cause change WITHIN system && forms of energy==[kinetic, potential, thermal, chemical, ... [TYPES]] && conservation of energy==law STATING energy CANNOT be created OR destroyed ONLY transformed BETWEEN forms && energy sources==[fossil fuels, nuclear, solar, wind, ... [
EXAMPLES]] USED TO power human activities"
  }
```


```
  {
    "instruction": "Define bits",
    "input": "",
    "output": "Bit AS basic unit of information IN digital computing AND communications REPRESENTING binary values [0, 1] && bits USED TO encode data AND instructions IN digital systems && multiple bits COMBINED INTO larger units SUCH AS [bytes, kilobytes, megabytes, ... [SIZES]] && bit rate==measure of data transf
er speed IN bits per second (bps)"
  }
```

```
  {
    "instruction": "Explain intentional programming",
    "input": "",
    "output": "Intentional Programming AS software development approach FOCUSING ON capturing developer's intent AND maintaining high-level abstractions THROUGHOUT development process && intentional code==code REPRESENTING developer's intent IN human-readable form && transformation engine==tool CONVERTING intention
al code INTO executable code && benefits==[improved maintainability, increased collaboration, ... [ADVANTAGES]] DUE TO explicit representation of intent"
  }
```

```
  {
    "instruction": "Describe partnership",
    "input": "",
    "output": "Partnership AS arrangement BETWEEN two OR more parties TO cooperate AND share resources, responsibilities, AND benefits IN pursuit of common goals && types of partnerships==[business, research, educational, ... [VARIETIES]] WITH different objectives AND structures && partnership agreements==legal doc
uments OUTLINING terms, responsibilities, AND profit-sharing arrangements BETWEEN partners"
  }
```

```
  {
    "instruction": "Explain polynomials",
    "input": "",
    "output": "Polynomials AS algebraic expressions THAT involve variables AND coefficients RAISED TO non-negative integer powers AND can be written IN the form a_nx^n + a_{n-1}x^{n-1} + ... + a_1x + a_0, WHERE a_n, a_{n-1}, ..., a_1, a_0 ARE constants && degree OF the polynomial IS the highest power OF the variabl
e IN the expression && polynomials USED TO model real-world situations INVOLVING multiple terms AND variables"
  }
```
**The file data-foundation.json is the file used to fine-tune a model to being able to extract more terms**

## Research State
I think the AI is capable of in-context learn this format, and in a training session it is much faster and efficient. The tokenizer behind this is larger than usual.

Some of its particulars:
* Introduces condensation masking with `...`
* Introduces hints keywords. example: `[ADVANTAGES]`, `[CHARACTERISTICS]`, `[RULES]`.
* Introduces directional keywords. example: `AS`, `AND`, `IN`, `BETWEEN`, `RANGING`.
* Introduces approach keywords. example: `NOTATED`, `PREDICTING`, `CALCULATED`
* Introduces efficient aggrupations keyword `===`
* Introduces separated relationship keyword `&&`

What it tries to preserve:
* The use of natural language words
* Instruction mode

What it tries to accomplish:
* Reasoning
* Relationship
* Condensation
* Size efficiency
* Faster reasoning
* Higher accuracy

# Progress Log
- 2023-05-20 - Released the first version of the dataset, illustrative examples.
- 2023-05-21 - Added the original foundation prompts that shaped the first dataset.
- 2023-05-21 - Added the first 3000 dataset items under `data/` folder. They will be marked with the date of the dataset version.
- 2023-05-22 - Added a new dataset that combines more exemplars together with CoNaLa dataset. The result is a model that can have conversations, follow instructions, produce TOK statements, and generate decent code as well.
- 2023-05-23 - Testing dataset combinations
- 2023-05-27 - Some testings proves LiMA effect, more is not better. At this point, cleaning or refining some of the notorious Datasets is highly relevant for a mixture. Combinations: CoT, SuperCoT, CoNaLa, AlpacaCode, GSM8k on 13B and 30B. Results are diverse and will be released at some point when are cleaned.

`For now the data files will be named with the date, and it will hold the whole dataset for now. In the future, once is cleaned and validated, it will be consolidated, deduplicated, and split into smaller files.`

## Information
* The dataset is not yet complete, it is a work in progress and looking for collaborators.
* The dataset is been tested at small scale: 100 examples were enough to fine tune a LLaMA 30Bmodel on a RTX40490 w/LoRA in a few minutes.
* The dataset named `foundation` data is the original prompts used to create the extraction process.
* The dataset structure will be fixed in field, but may be subject of changes within the input and instruction.

# Next Steps
* Keep generating more datafor the set. Phase 1 is 1 keyword. --> PAUSED `reformulating how the ideal dataset syntax will be`
* llama-30b-4bit on a combined AutoCoT 100%+COT (Complete) Shuffle 30% + TOK 100%
* Get a smaller model, updated corpus and extract valuable knowledge from it.
* Load the new updated data (2023) and FineTune an older (2021) and validate update process. 
* Generate more data for the set. Phase 2 is 2 keywords
* Isolate `TOK` output style with a special character.
* Add `LEAF` `TREE` `EXPAND` and `CONTEXT` flavours --> EXPERIMENTING

## Experiment Notes
* It would be ideal to combine this with other datasets. Ideally if the model can understand that the shape of this set is knowledge and not conversation then it would allow incremental efficient learning.
* llama-13b-4b with the 20230522 dataset produced much better TOK descriptions
* llama-13b-4b with the 20230522 & CoNaLa was able to have normal conversation, produce coherent code in several languages, output TOK syntax and overall shows a good reasoning but not good math.
* llama-30b-4bit with 3k TOK improved the quality of TOK itself, so a new dataset generation will be released soon

- 230522 Fine tuned llama-13b-4bit with this dataset and conala, the model is able to chat, generate code, and generate TOK. The TOK seems better furnished compared with llama-30b-4bit with only foundation.
- 230522 I will upload separately the new set instructions generated by the finetuned model.
- 230523 Funky result on a tiny model: 7b was trained on TOK. His math was very bad, but the reasoning was very good. Reinforced on GSM8k produced a good result.
- 230523 

## Citations

Please cite this repository if you use our code.

```
@misc{tree-of-knowledge,
  author = {Xavier M},
  title = {Tree of Knowledge: ToK aka Tree of Knowledge dataset for Large Language Models LLM,
  year = {2023},
  publisher = {GitHub},
  journal = {GitHub repository},
  howpublished = {\url{https://github.com/fblgit/tree-of-knowledge}},
}
```
