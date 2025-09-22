
Introduction
------------

Collects prompt engineering practices with Claude LLM. 

![Prompt-Optimization-HLD](./docs/HLD-0-Prompt_Optimization_Flow.png)

One approach is to automate prompt refinement iterations programmatically.

![Prompt_Optimization.ipynp](./Prompt_Optimization.ipynb) walks tough an example. 
There are many moving parts in a prompt. 
A suitable framework needs to decompose all parts of prompt (system, assistant, output requirements, few samples, etc.)
so that a search algorithm could be developed. 

Utilized code in <a href="https://anthropic.skilljar.com/claude-with-the-anthropic-api/" target="_blank">Anthrophic Building with the Claude API</a> course. 
Refactored the code by using role based class representation.

<ul>
<li>TestSuiteGenerator: Generates test prompts with different inputs for the **same prompt**  
<li>PromptOutputGrader: Execute test prompts, and grade completions. 
<li>EvaluationWriter: Writes the evaluation results into HTML file so that we can compare. 
<li>AntrophicClient: Encapsulates Anthrophic API client. Intent is able to test with different LLM (Claude, OpenAI, Gemini,...) and model combinations.
<li>AntrophicPrompt: This should accumulate messages and should be an abstraction for a prompt eventually with a better name. 
</ul>

There is no concern with separation of duties because TestSuiteGenerator and PromptOutputGrader uses the same Claude model ().


Another approach is to state prompt refinement as an optimization problem 
hence one can put **prompt refinement** in an optimization framework to search for an optimal prompt.
Evolutionary algorithm approach[1] is applicable for emulating iterative evolution of prompt population to find a set of high performing prompts. 
Clear definition of prompt representation will help to define mutation and cross-over operations. 
One approach is we can utilize LLM to mutate a prompt or cross-over two prompts to obtain new offspring prompts. 
Then, EA applies selection to build the next generation of prompts. 

References
----------
1. [An LLM-Based Genetic Algorithm for Prompt Engineering](https://dl.acm.org/doi/10.1145/3712255.3726633)
1. [EvoPrompt - A Game Changer for Optimizing AI Interactions](https://news.promptengineering.org/evoprompt-a-game-changer-for-optimizing-ai-interactions.html)
1. [Evolving Prompts with Genetic Algorithms: A Novel Approach to Prompt Engineering](https://medium.com/@eugenesh4work/evolving-prompts-with-genetic-algorithms-a-novel-approach-to-prompt-engineering-a2e1e0f53b9a)
1. [Connecting Large Language Models with Evolutionary Algorithms Yields Powerful Prompt Optimizers](https://openreview.net/pdf?id=ZG3RaNIsO8)
1. [EvoPrompt – Evolutionary Algorithms Meets Prompt Engineering. A Powerful Duo](https://ai.gopubby.com/evoprompt-evolutionary-algorithms-meets-prompt-engineering-a-powerful-duo-c30c427e88cc)
1. [EvoPrompt Implementation](https://github.com/beeevita/EvoPrompt)
1. [GAAPO: Genetic Algorithmic Applied to Prompt Optimization](https://arxiv.org/abs/2504.07157)
1. [DSPy](https://arxiv.org/abs/2310.03714) 
1. [DSPy Implementation](https://github.com/stanfordnlp/dspy)
1. HOPR (Hint Optimization and Prompt Refinement)
1. [GEPA: Reflective Prompt Evolution Can Outperform Reinforcement Learning](https://arxiv.org/abs/2507.19457)
1. [Building the Entire RAG Ecosystem and Optimizing Every Component](https://levelup.gitconnected.com/building-the-entire-rag-ecosystem-and-optimizing-every-component-8f23349b96a4)