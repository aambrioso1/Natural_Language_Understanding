# Natural_Language_Understanding

A repository of notes and information related to Natural Language Understanding.   My intention is to focus on large language models and their emerging ability learn from explanations (few-shot prompting).

Here is a set up papers that cover this area:

https://www.gwern.net/docs/ai/gpt/inner-monologue/index

Here is a quote from the first paper on the list, ["Can Language Models learn from explanations in context?"](https://arxiv.org/pdf/2204.02329.pdf),

"A new paradigm has emerged in natural language processing: few-shot prompting of large language models. Such models appear to exhibit some in-context learning abilities, such that they can infer how to perform a new language task few-shot from a few examples of input and output pairs within the model’s context window, but without training."

Other papers to look at:
* https://arxiv.org/abs/2005.14165
* https://github.com/google/BIG-bench/
* https://aclanthology.org/2021.acl-long.90.pdf
* https://arxiv.org/pdf/2205.01068.pdf


### Notes on ["Can Language Models learn from explanations in context?"](https://arxiv.org/pdf/2204.02329.pdf)

The first paper on the Gwern's inner-monologue list.   Here is a quote that describes there area of study the paper seeks to advance.

"A new paradigm has emerged in natural language processing: few-shot prompting of large language models. Such models appear to exhibit some in-context learning abilities, such that they can infer how to perform a new language task few-shot from a few examples of input and output pairs within the model’s context window, but without training."

Another interesting way to look at this is to think of it as the beginning of a new language between human beings and large language models (LLMs).   Even more interesting is that the communication could continue to improve.   Both human being and the future LLMs are in a sense learning to communicate with each other.   As we figure out how to better explain a task will future LM give us verbal direction as to what information they need to solve a problem.   Will the emergent behaviour resembly human language development?   There are four scales of time to consider here:  (1) the infant learning language and (2) the child learning more language skills (4) the more nuisance learning involved in more mature language skills like essay writing and story telling and (4) the human species learning language through evolution. 

Care must be taken when creating prompts. From the abstract of [True Few_shot Learning with Language Models](https://arxiv.org/abs/2105.11447):

"Overall, our findings suggest that prior work significantly overestimated the true few-shot ability of LMs given the difficulty of few-shot model selection.""

About models used in the "Can Models learn ..." paper:

"We evaluated a set of large language models ranging from 1 billion to 280 billion parameters (Rae et al., 2021). These models differ in architectural features such as the number of layers and embedding size, but crucially (that is ... "in order to minimize confounding" [my editorial comment]) have been trained on the same quantity of the same dataset, with equivalent context windows."

The research used a variety of control conditions:
* tuned and untuned explanations
* scrambling explanations at a word level
* scrambling explanations
* using true non-explanations
* annotating tasks with non-instructions.

Use 0-shot to 5-shot prompts (the limit to 5 is somewhat arbitrary but necessary [my note]) for various combinations of task instructions (none, task instructions, or non-instruction) and explanantion types (none, other item explanation, true non-explanation, or scrambled explanation)

"Indeed, a human might ask for clarification of a confusing explanation, but our models do not have that opportunity or ability. To provide some insight into the potential benefits of more optimal explanations, we conducted two tuning experiments [p. 6]."

Here is an interesting point.   What sort of design would allow a LM with NLG ability to ask for clarification?   Perhaps simply ask the model, "Do you have any questions", as part of a dialogue.

Start on page 6 here:  "Second we hand-tuned the explanations from prompts for five tasks ..."




