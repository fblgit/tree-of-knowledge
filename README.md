# tree-of-knowledge-llm
ToK aka Tree of Knowledge for Large Language Models LLM. It's a novel dataset that inspires knowledge symbolic correlation in simple input and output prompts.

Can these two be put together?

* https://arxiv.org/pdf/2305.10601.pdf
* https://arxiv.org/pdf/2305.08298v1.pdf

I am not an expert on this, but I tried to make some experiments for the last few months. Maybe you can put it to a more strong test?

Here are some examples in different disciplines:

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

## Research State
I think the AI is capable of in-context learn this format, and it a training session it is much faster and efficient. The tokenizer behind this is large than usual. 
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


















