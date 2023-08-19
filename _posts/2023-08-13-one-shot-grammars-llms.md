---
layout: distill
title: 'Zero-Shot Grammars: Teaching LLMs Novel Programming Languages On-The-Fly'
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
      * [Toolformer](https://arxiv.org/abs/2302.04761) <d-cite key="schick2023toolformer"></d-cite>
      * [Synchromesh](https://arxiv.org/abs/2201.11227) <d-cite key="poesia2022synchromesh"></d-cite>
        * Target Similarity Tuning: Dynamically select semantically-relevant examples for a given description
          * Rank by tree edit distances for ASTs
        * Constrained Semantic Decoding: Enforce rich semantic and syntactic constraints during code generation on top of a frozen language model
          * Unconstrained language models use undeclared variables, lose track of nesting levels, or call fns with arguments of the wrong type
        * Completion Engines - abstraction over above
          * Layer 1: Context-free layer, which enforces syntactic validity
          * Layer 2: Context-sensitive layer, encodes constraints based on language and user's constraints
        * !!!! Provide a library to enumerate possible completions from an ANTLR grammar
        * Brzozowski derivatives to figure out completions


    * Summaries
      * [SQL generation](https://blog.langchain.dev/llms-and-sql/)
      * Regular expressions
    * Papers
      * [Flexible Grammar-Based Constrained Decoding for Language Models](https://arxiv.org/abs/2305.13971)<d-cite key="geng2023flexible"></d-cite>
      * [Constrained Language Models Yield Few-Shot Semantic Parsers](https://arxiv.org/abs/2104.08768) <d-cite key="shin2021constrained"></d-cite>
      * [PICARD: Parsing Incrementally for Constrained Auto-Regressive Decoding from Language Models](https://arxiv.org/abs/2109.05093) <d-cite key="scholak2021picard"></d-cite>
      * [Grammar prompting](https://arxiv.org/abs/2305.19234) <d-cite key="wang2023grammar"></d-cite>
        * semantic parsing (SMCalFlow,Overnight,GeoQuery), PDDL planning, molecule generation(SMILES).
        * Constrained decoding: LR early parser is intractable because of multi-token continuations and the need to call the LLM API on every time step
        * Speculatively generate an entire continuation, if it parses return, otherwise use Earley LR parser to find longest valid prefix
        * Experiments:
          1. Standard prompting
          2. Standard prompting w/ constrained generation
          3. Derivation tree-based prompting
        * Codex as base LLM for experiments
        * TODO: I understand the constrained generation part, but I don't really understand their prompting scheme and how getting the LLM to generate a grammar works
      * Symbolic reasoning papers
        * [Solving Math Word Problems by Combining Language Models With Symbolic Solvers](https://arxiv.org/abs/2304.09102) <d-cite key="heyueya2023solving"></d-cite>
        * [Faithful Chain-of-Thought Reasoning](https://arxiv.org/abs/2301.13379) <d-cite key="lyu2023faithful"></d-cite>
        * [Chain-of-Symbol Prompting Elicits Planning in Large Langauge Models](https://arxiv.org/abs/2305.10276) <d-cite key="hu2023chainofsymbol"></d-cite>
        * [Satisfiability-Aided Language Models Using Declarative Prompting](https://arxiv.org/abs/2305.09656) <d-cite key="ye2023satisfiabilityaided"></d-cite>
        * [Logic-LM: Empowering Large Language Models with Symbolic Solvers for Faithful Logical Reasoning](https://arxiv.org/abs/2305.12295) <d-cite key="pan2023logiclm"></d-cite>
      * OpenAI plugin as zero-shot/few-shot semantic parser https://platform.openai.com/docs/plugins/examples
      * Neural parameterization of symbolic grammars
        * [Unsupervised Neural Dependency Parsing](https://aclanthology.org/D16-1073/) <d-cite key="jiang-etal-2016-unsupervised"></d-cite>
          *
        * [Recurrent Neural Network Grammars](https://arxiv.org/abs/1602.07776) <d-cite key="dyer2016recurrent"></d-cite>
        * [Unsupervised Recurrent Neural Network Grammars](https://aclanthology.org/N19-1114/) <d-cite key="kim-etal-2019-unsupervised"></d-cite>
        * [Compound Probabilistic Context-Free Grammars for Grammar Induction](https://aclanthology.org/P19-1228/) <d-cite key="kim-etal-2019-compound"></d-cite>
        * TODO: go back to https://arxiv.org/abs/2305.19234 and fetch more for this list if relevant
      * Embedded neural components in synchronous grammars
        * [Sequence-to-Sequence Learning with Latent Neural Grammars](https://arxiv.org/abs/2109.01135) <d-cite key="kim2021sequencetosequence"></d-cite>
        * [Finding Dataset Shortcuts with Grammar Induction](https://arxiv.org/abs/2210.11560) <d-cite key="friedman2022finding"></d-cite>
        * [Hierarchical Phrase-based Sequence-to-Sequence Learning](https://arxiv.org/abs/2211.07906) <d-cite key="wang2022hierarchical"></d-cite>


## Keywords

* Natural Language Generation
* Program synthesis
* Semantic parsing
* In-context learning
* Neural parameterization of Symbolic Grammars

# Grammar choices

* BNF
* ANTLR

## Recurrent Language Design

Grammar <=> Examples

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
