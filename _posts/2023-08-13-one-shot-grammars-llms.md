---
layout: distill
title: 'Zero  -Shot Grammars: Teaching LLMs Novel Programming Languages On-The-Fly'
date: 2023-08-13

authors:
  - name: James Reed
    url: https://jameskreed.com
    affiliations:
      name: Independent

bibliography: 2023-08-13-one-shot-grammars-llms.bib

---

## Related work
  * Code generation ability
    * Code-specific models
      * [CodeGen](https://github.com/salesforce/CodeGen)
      * [StarCoder](https://huggingface.co/blog/starcoder)
    * General-purpose models
      * GPT-*
  * Constrained Generation
    * Projects
      * [jsonformer](https://github.com/1rgs/jsonformer)
      * [guidance](https://github.com/guidance-ai/guidance)
    * Summaries
      * [SQL generation](https://blog.langchain.dev/llms-and-sql/)
    * Papers
      * [Flexible Grammar-Based Constrained Decoding for Language Models](https://arxiv.org/abs/2305.13971)<d-cite key="geng2023flexible"></d-cite>
      * [Constrained Language Models Yield Few-Shot Semantic Parsers](https://arxiv.org/abs/2104.08768)
      * [PICARD: Parsing Incrementally for Constrained Auto-Regressive Decoding from Language Models](https://arxiv.org/abs/2109.05093)
      * [Grammar prompting](https://arxiv.org/abs/2305.19234)
        * semantic parsing (SMCalFlow,Overnight,GeoQuery), PDDL planning, molecule generation(SMILES).
        * Constrained decoding: LR early parser is intractable because of multi-token continuations and the need to call the LLM API on every time step
        * Speculatively generate an entire continuation, if it parses return, otherwise use Earley LR parser to find longest valid prefix

## Solving the Tokenization Problem?

* Grammar lexemes != LLM (BPE) tokens

## One-Shot Prompting with BNF
  * Test harness, evaluation
  * Results
  * Lack of syntactic prompting

## Further Prompt Engineering

## Explicit Constrained Generation

### Model Size Reduction Due To Constrained Generation

## Language Explicitly Designed for Prompted Decoding
