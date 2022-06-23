# Natural_Language_Understanding

A repository of notes and information related to Natural Language Understanding.   My intention is to focus on large language models and their emerging ability learn from explanations (few-shot prompting).

Here is a set of papers that cover this area:

https://www.gwern.net/docs/ai/gpt/inner-monologue/index

Other papers to look at:
* https://arxiv.org/abs/2005.14165
* https://github.com/google/BIG-bench/S
* https://aclanthology.org/2021.acl-long.90.pdf
* https://arxiv.org/pdf/2205.01068.pdf
* [Rethinking the Role of Demonstrations:  What Makes In-Context Learning Work?] https://arxiv.org/pdf/2202.12837.pdf


### Notes on ["Can language models learn from explanations in context?"](https://arxiv.org/pdf/2204.02329.pdf)

This first paper on the Gwern's inner-monologue list.   Here is a quote that describes the area of study the paper seeks to advance.

#####  1. Introduction
"A new paradigm has emerged in natural language processing: few-shot prompting of large language models. Such models appear to exhibit some in-context learning abilities, such that they can infer how to perform a new language task few-shot from a few examples of input and output pairs within the model’s context window, but without training."

Another interesting way think about this is that it is the beginning of a new language between human beings and large language models (LLMs).   This communication could continue to improve.   Both human being and the future LLMs are in a sense learning to communicate with each other.   As we figure out how to better explain a task will future LMs give us verbal direction as to what information they need in order to solve a problem.   Will the emergent behaviour resemble human language development?   There are four scales of time to consider here:  (1) the infant learning language and (2) the child learning more language skills (4) the more nuisance learning involved in mature language skills like essay writing and story telling and (4) the human species learning language through evolution. 

Care must be taken when creating prompts. From the abstract of [True Few-Shot Learning with Language Models](https://arxiv.org/abs/2105.11447):

"Overall, our findings suggest that prior work significantly overestimated the true few-shot ability of LMs given the difficulty of few-shot model selection.""


##### 2. Methods

The researchers used the [BIG-BENCH Colloboration](https://github.com/google/BIG-bench/) for a challenging set of tasks.  Chose a subset of 40 tasks and subtask involving a variety of skills

About models used in the "Can Models learn ..." paper:

"We evaluated a set of large language models ranging from 1 billion to 280 billion parameters (Rae et al., 2021). These models differ in architectural features such as the number of layers and embedding size, but crucially (that is ... "in order to minimize confounding" [my editorial comment]) have been trained on the same quantity of the same dataset, with equivalent context windows."

The researchers used a variety of control conditions:
* tuned and untuned explanations,
* scrambling explanations at a word level,
* scrambling explanations,
* using true non-explanations, and
* annotating tasks with non-instructions.

The research team used 0-shot to 5-shot prompts to create various combinations of task instructions:
* none, 
* task instructions, or 
* non-instruction). 

and explanantion types:
* none, 
* other item explanation, 
* true non-explanation, or
* scrambled explanation.  

The limit to 5 is somewhat arbitrary but necessary to allow for fair performance comparisons.

"Indeed, a human might ask for clarification of a confusing explanation, but our models do not have that opportunity or ability. To provide some insight into the potential benefits of more optimal explanations, we conducted two tuning experiments [p. 6]."

This brings to mind some interesting ideas.   What sort of design would allow an LLM to use its NLG ability to ask for clarification?   Could we tune the LM to ask good questions?  Perhaps one could simply ask the model, "Do you have any questions", as part of a dialogue.

Explanations were hand-tuned to try to improve performance.   Examples of tuned and untuned explanations and of lessons learned are give in Appendix B.4.

To measure the effects of different components of the prompts on performace methodes of hierchical/multilevel modeling were used (Gelman and Hill, 2006).

Their methods produced:
* a parameter fro the difficulty of each task,
* a parameter for the difficulty of each question within a tasks, and
* a parameter for how wach distinct set of explanations affects performance.

##### 3. Results
The predicted performance of the largest model is presented in the body of the paper (Gopher, with 280 Billion parameters).

* Few-shot examples substantial improve performace relative to zero-shot.
* Untuned explanations improve performance with about 1/3 the effect of few-shot examples.
* Instructions improve performance but less than explanations.
* Examples and explanations together offer more substantial benefits than examples alone.
* Hand-tuning offers substantial benefit on tasks where it was tried
* The benefit of untuned explanations does not vary in prompts or with or without task instructions or non-instructions.
* Only large models benefit from explanations.
* Control explanations and non-explanations are neutral or harmful for the largest model.
* Untuned explanations significantly outperform all control conditions for the largest models.
* Results seem to be consistent across different tasks types (Section 3.3)

##### 4.  Related Work
* Learning shown by LLMs is a form of implicit Bayseian inference.
* Are LLMs learning or are they simpley "recoverying previously-experienced tasks." [p. 8]
* Task instructions as zero-shot prompts or part of a few-shot prompt.
* Explicitly decomposing problems into steps. (Mishra et al. 2021a) 
* "Task prompt can be worth many examples"
* Prompts with task descriptors and example with explanations.
* Few shot prompting to have modes explain their answer for user interpretability not for improved performance (Marasovic et al. 2021)
* Models can benefit from examples that decompose the reasoning process (Wei et al, 2022)
* Using "external scratchpads" to store and remember intermediate computations
* This work provides explanations after the answer in the prompt rather than before.
* Training LMs with instructions or explanations.
* Explanations can be used in other domains like for computer vision, mathematics problem-solving, relational reasoning, and reinforcement learning
* Sharp transitions due to increasing model size have been observed and discussed.

Quote:  "future larger models may exhibit yet larger benefits (p. 10)"

##### 5. Discussion

* Can explanations improve few-shot learning?  Yes
* Why are post answer explanations interesting? The authors contrast pre-answer chains-of-reasoning with post answer explanations:
	* Some explanations are holistic and only make sense if the answer is known
	* The beneficial effect of explanations must be due to higher order inferences.
* What do our results imply about an LMs' abilities for in-context learning?   The technique using matched controls in this research allowed the to test whether superficial features were responsible for the improved performance.   The LM show a significate advantage for real explanations.
* How do explanations relate to task instruction?  The benefits are similar and complementary.
* What are the benefits and draw backs ofr the datasets used?  BIG-Bench provided a set of diverse and challenging tasks involving skills that are not typically representated in standard datasets.   But these task may not represent the kinds of task LMs are typically used for.   "Future work should explore the benefits of explanations beyond BIG-Bench. [p. 12]"

This question is very relavant to work in the AMHR lab so I have quoted their response.
"What is the relationship to human language processing? Given that we were inspired by work in cognitive psychology on human use of explanations (e.g. Ahn et al., 1992; Lombrozo and Carey, 2006), and given the accumulating evidence that language models predict language processing in the human brain to a surprising degree (Goldstein et al., 2022; Schrimpf et al., 2021), it is natural to ask whether there are cognitive implications of our experiments. However, as we noted above, the fact that both language models and humans benefit from explanations does not imply that they necessarily benefit through the same mechanisms. Indeed, the benefits of explanations that we observed are smaller than one might expect for humans. However, note that many of our tasks, such as evaluating mathematical induction arguments, would be challenging for many humans, even with instructions, examples, and explanations. Differences between humans and model responses to explanations may be due in part to the fact that language models lack the broader context in which humans process language—language models do not directly experience the situations and relationships to which language refers (McClelland et al., 2020). Furthermore, human explanations are fundamentally pragmatic and communicative (Cassens et al., 2021; Van Fraassen, 1988)—they are intended to convey a particular meaning in a particular context, and are often part of a broader dialogue. It is likely that the reasoning processes humans engage to understand an explanation are shaped by this interactive experience. Thus, models trained in richer, more interactive settings might benefit more from explanations (Santoro et al., 2021). Reciprocally, explanations could provide an interesting setting for future work investigating the similarities and differences between the human and model language processing." [p. 12] 
* What are the benefit of our research and analytic methods?   Researchers should consider using heirarchical/multilevel regression models.   See [Data Analysis using Regression and Multilevel/Hierarchical Models] (https://www.cambridge.org/highereducation/books/data-analysis-using-regression-and-multilevel-hierarchical-models/32A29531C7FD730C3A68951A17C9D983#overview)

Authors mention an interesting paper that suggest that LMs are lazy.  They use superficial features, unless the task is more challenging.  [When Classsifying Arguments ...](https://scholarworks.umass.edu/cgi/viewcontent.cgi?article=1244&context=scil)


##### 6. Conclusions   
* Explanations are beneficial.   Tuned explanations are better but untuned explanations out perform controls.

Again the language here is pretty perfect so I quote:
...only large models can benefit from explanations—this capability is emergent. These results have implications not only for designing better language model prompts, but also for scientific understanding of the in-context learning abilities exhibited by language models.

The second paper on Gwern's list:
### [SOCRATIC MODELS: COMPOSING ZERO-SHOT MULTIMODAL REASONING WITH LANGUAGE”, ZENG ET AL 2022](https://arxiv.org/pdf/2204.00598.pdf)

"In this work, we propose that these model differences are complementary (VLMS and LMS), and can be jointly leveraged
to build AI systems with structured Socratic dialogue – in
which new multimodal tasks are formulated as a guided exchange between different pre-existing language-based foundation models, without additional finetuning" [p. 1]

"In the context of egocentric perception, we present a case study of Socratic Models (SMs) that can provide meaningful results for complex tasks such as generating free-form answers to contextual questions about egocentric video, by formulating video Q&A as short story Q&A, i.e. summarizing the video into a short story, then answering questions about it. Additionally, SMs can generate captions for Internet images, and are competitive with state-of-the-art on zero-shot video-to-text retrieval with 42.8 R@1 on MSR-VTT 1k-A. SMs demonstrate how to compose foundation models zero-shot to capture new multimodal functionalities, without domain-specific data collection." [From the Abstract]

Socratic Models (SMs) are a class of systems that embrace the zero-shot capabilities of foundation models by engineering guided discussions between the
independent models to reach a shared consensus on a taskspecific output. SMs use language as the representation by which inter-domain foundation models can jointly be used
for inference. [p. 1]

They use Visual Languge Models (VLMs), Language Models (LMs), and Audio Language Models (ALMs) together to perform NLU tasks.

They call the system egocentric since the language generated by the LM is in first person.   It makes sense that a first person perspective would pull the LM's responses to appropriate context in its language distribution.

It would be interesting to see of another perspective would lead to poorer performance.

If an LM can tell a story why can't that story be about reality?   The answer seem to be that it can!

"SMs use language as the representation by which inter-domain foundation models can jointly be used
for inference." [p. 1]

It seem that not only are we learning to communicate with LMs different NLU system are learning to communicate with each other!

Some ideas:
(1)  Story-telling as reasoning.
(2)  Training LM on audio with emotional content and using this to enhance an SM.
(3)  Testing the effectiveness of egocentric language.

There "highlight" aaplication is open-ended reasoning about egocentric perception.

"We find that simple scripted policies to guide a closed-loop exchange between pre-trained LM, VLM, and ALM models can (a) generate meaningful captions that respond to questions like “what am I doing?” with answers like “receiving a package” that span beyond the label set of standard vision datasets (Sigurdsson et al. 2018; Smaira et al. 2020), and (b) exhibit open-ended contextual Q&A capabilities previously thought to be out-of-reach for egocentric perception without domain-specific data collection." [p. 2]


Contributions of this paper"
(1)  The SM framework.
(2)  demonstraiton of an egocentric perception system using SMs.
(3)  qualitative results on video understanding that is not covered by existing benchmarks.
(4)  quantitative comparison to SOA visual understanding models using the MSR-VTT datset for video-to-text retrieval.
(5)  a framework for unsupervised quantitative model selection of SMs through sub-model ablations.

Language can be used to compose existing models.

This is a very attractive idea.   LMs trained for NLG should be able to demonstrate reasoning ability that can be leveraged to interpret any information.

For open-ended reasoning, a key aspect of our approach is
formulating video understanding as reading comprehension,
i.e. re-frame “video Q&A” as a “short story Q&A” problem,
where the language-based world-state history can be viewed
as an interpretable state representation in the form of short
stories, which can be used for reading comprehension Q&A,
for which LMs have demonstrated strong zero-shot performance

Section 3.3:  Language-based World_State History from Video

This section gives examples of how the LMs reasoning ability is used to guide the VLMs choices of activities. 

Start with Appendix D
Appendix D has a discussion of egocentric perception.


















