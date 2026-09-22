# SECTION 1 — AI & GENERATIVE AI (30 Questions)

### Q1. Which statement correctly describes the relationship between AI, Machine Learning, and Deep Learning?

A. Deep Learning is a subset of Machine Learning, which is a subset of Artificial Intelligence

B. Machine Learning is a subset of Deep Learning, which is a subset of Artificial Intelligence

C. Artificial Intelligence is a subset of Machine Learning

D. They are three independent, unrelated fields

**Correct Answer:** A

**Difficulty:** Easy

**Topic:** AI vs ML vs Deep Learning

**Explanation:**
AI is the broadest field (machines simulating human-like intelligence). ML is a subset of AI in which systems learn patterns from data, and Deep Learning is a subset of ML using multi-layer neural networks. So the correct containment order is Deep Learning ⊂ ML ⊂ AI.

**Why the other options are wrong:**
- B: Reverses the containment hierarchy.
- C: AI is the superset, not the subset.
- D: Deep Learning, ML, and AI nest inside one another.

**Key Concept:** Remember the nesting: Deep Learning ⊂ Machine Learning ⊂ AI.

---

### Q2. What best defines Generative AI?

A. A system that only classifies or predicts categorical labels

B. A type of AI that creates new content (text, images, audio) by modeling patterns in training data

C. A database that stores AI-generated outputs

D. A rule-based expert system that follows hand-written rules

**Correct Answer:** B

**Difficulty:** Easy

**Topic:** Generative AI Fundamentals

**Explanation:**
Generative AI learns the underlying distribution of training data and samples new, plausible content from it, such as paragraphs, images, or code. Classification/prediction systems decide on existing inputs rather than producing new data.

**Why the other options are wrong:**
- A: Describes discriminative/traditional ML.
- C: Storage is not generation.
- D: Rule-based expert systems are not learned generative models.

**Key Concept:** Generative = produces new data; predictive/discriminative = decides about existing data.

---

### Q3. Which of the following outputs is the best example of a Generative AI capability?

A. Predicting tomorrow's sales from six months of revenue history

B. Sorting incoming emails into folders based on labels

C. Writing a coherent full-length paragraph summarizing a document it has never 'seen' in chat, in a consistent tone

D. Approving a loan application when a credit score exceeds a threshold

**Correct Answer:** C

**Difficulty:** Easy

**Topic:** Generative AI Fundamentals / Distinguishing Generation vs Prediction

**Explanation:**
Writing a new coherent paragraph is data generation — creating content that did not exist. Predicting sales, classifying emails, and threshold-based loan approval are discriminative/predictive tasks that map inputs to decisions.

**Why the other options are wrong:**
- A: Regression/prediction.
- B: Classification.
- D: Rule-based decisioning.

**Key Concept:** A generative output is new content, not a label or number assigned to an input.

---

### Q4. In modern image generation, what does a "diffusion model" primarily do?

A. Performs optical character recognition on images

B. Compresses images losslessly for storage

C. Classifies images by their content

D. Starts from random noise and iteratively removes noise to form a coherent image

**Correct Answer:** D

**Difficulty:** Easy

**Topic:** Generative AI — Diffusion Models

**Explanation:**
Diffusion models are trained to reverse a noise-adding process. At inference, they begin with pure random noise and denoise it step by step toward a clean image matching a text/semantic condition. OCR, compression, and classification are not generative synthesis.

**Why the other options are wrong:**
- A: OCR is extraction, not generation.
- B: Compression is not generation.
- C: Classification is discriminative.

**Key Concept:** Diffusion = progressive denoising of random noise into content.

---

### Q5. Which distinction between traditional ML and Generative AI is most accurate?

A. Traditional ML learns a decision boundary to predict outputs; Generative AI models the data distribution to sample new data

B. Generative AI always only predicts labels

C. Traditional ML models can generate arbitrary new images

D. Neither approach can learn from data

**Correct Answer:** A

**Difficulty:** Easy

**Topic:** Traditional AI vs ML vs GenAI

**Explanation:**
Discriminative (traditional) models approximate P(label | input) — a boundary that separates/classifies. Generative models approximate P(data) — the distribution itself — allowing them to sample brand-new plausible data. Both learn from data.

**Why the other options are wrong:**
- B: Generation is about producing new data, not predicting labels.
- C: Traditional models map input to output; they do not synthesize new images.
- D: Both learn from data.

**Key Concept:** Predictive draws a boundary; generative learns the distribution.

---

### Q6. A language model produces a fluent, confident, and grammatically perfect paragraph that contains a factual claim that is completely false. What is this phenomenon called?

A. Overfitting

B. Hallucination

C. Model underflow

D. Prompt truncation

**Correct Answer:** B

**Difficulty:** Easy

**Topic:** Hallucination

**Explanation:**
A hallucination is content generated by the model that is fluent and plausible but factually false or unfounded — often because tokens are predicted by probability, not by truth-checking. Overfitting is memorization of training data, not the production of confident falsehoods.

**Why the other options are wrong:**
- A: Overfitting is a training behavior unrelated to invented facts.
- C: Underflow is a numeric issue.
- D: Truncation would cut content, not invent facts.

**Key Concept:** Fluent + confident + false = hallucination.

---

### Q7. A medical team builds (1) a classifier that detects diabetic retinopathy from retinal scans and (2) an LLM that drafts patient-friendly explanations of treatment plans. How should these two systems be categorized?

A. (1) Generative AI; (2) Traditional ML

B. Both are Generative AI

C. (1) Traditional ML; (2) Generative AI

D. Both are discriminative classifiers

**Correct Answer:** C

**Difficulty:** Moderate

**Topic:** AI vs ML vs GenAI — Identification

**Explanation:**
Detecting a condition from a scan is a classification (discriminative) task — mapping input to a label. Drafting text descriptions is generative — creating new natural-language content. This hybrid setup is very common in healthcare.

**Why the other options are wrong:**
- A: Reverses the two classifications.
- B: The detector does not create new data.
- D: The drafting system is not a classifier.

**Key Concept:** Classifier = discriminative; drafting new text = generative.

---

### Q8. Which of these tasks is NOT a typical use of Generative AI?

A. Drafting a personalized cover letter from a résumé

B. Summarizing a long news article

C. Recommending movies similar to a user's past ratings

D. Converting a natural-language request into runnable SQL

**Correct Answer:** C

**Difficulty:** Moderate

**Topic:** GenAI Use Cases vs Predictive ML

**Explanation:**
Movie recommendation from a user's rating history is collaborative filtering, traditionally a discriminative/recommender problem, not content generation. Drafting, summarizing, and NL-to-SQL are generative tasks.

**Why the other options are wrong:**
- A: Text generation.
- B: Condensed new text generation.
- D: Transformative content generation.

**Key Concept:** Recommendations from history are typically NOT a generative task.

---

### Q9. An LLM writes text by predicting, at each step, the most likely next token given all tokens produced so far. What is this generation strategy called?

A. Autoregressive generation

B. Diffusive denoising

C. Adversarial training

D. Discriminative labeling

**Correct Answer:** A

**Difficulty:** Moderate

**Topic:** LLM Generation Mechanics

**Explanation:**
Autoregressive models generate output sequentially: each token's probability depends on previous tokens. GAN adversarial training and diffusion are alternative paradigms; discriminative labeling is classification.

**Why the other options are wrong:**
- B: Diffusion denoising is used in image models/denoising, not next-token prediction.
- C: Adversarial training is a training method, not a generation strategy.
- D: Labeling is classification.

**Key Concept:** LLMs are autoregressive: next token given previous tokens.

---

### Q10. A marketing team wants an LLM to automatically write product descriptions for thousands of SKUs. What is the single most important operational requirement?

A. A human must review outputs for factual and brand-safety accuracy before publishing

B. The model will require no product-specific details in the prompt

C. All generated descriptions will be inherently factually correct

D. The tool will only work for image output

**Correct Answer:** A

**Difficulty:** Moderate

**Topic:** GenAI Deployment / Output Validation

**Explanation:**
The essential operational requirement is human validation: models make plausible but wrong statements about product specs, so someone must review outputs for factual and brand-safety accuracy before they are published.

**Why the other options are wrong:**
- B: Wrong — prompts must include the product-specific details the descriptions are based on.
- C: Wrong — generated descriptions are not inherently factually correct.
- D: Wrong — this use case is text, not image output.

**Key Concept:** Before publishing AI text, validate facts and tone.

---

### Q11. Which statement about an LLM's relationship to its training data is most accurate?

A. The model stores a complete copy of every training sentence in memory

B. The model's knowledge updates dynamically with every user query

C. The model's style and behavior reflect statistical patterns from training data, but it does not hold a faithful copy of the corpus

D. Training data has no observable effect on output style or vocabulary

**Correct Answer:** C

**Difficulty:** Moderate

**Topic:** Training Data vs Model Knowledge

**Explanation:**
An LLM encodes compressed statistical patterns from pretraining. It can reproduce fragments it saw often, but it does not keep a relational/factual store of the corpus, nor does it learn from individual queries.

**Why the other options are wrong:**
- A: No full copy is retained.
- B: Queries do not update weights.
- D: Training data strongly shapes style.

**Key Concept:** The model is a statistical summary of training data, not a database of it.

---

### Q12. A university builds an essay-grading tool where a human rubric is applied by teachers and a model scores drafts, with a professor approving final grades. What concept best describes this setup?

A. Fully autonomous Generative AI

B. Unsupervised learning

C. Relational database system

D. Human-in-the-loop AI system

**Correct Answer:** D

**Difficulty:** Moderate

**Topic:** Human Oversight

**Explanation:**
The professor approving final grades is a human-in-the-loop control: the AI assists, the human decides. Full autonomy, unsupervised learning, and database systems do not describe rubric-based grading with human approval.

**Why the other options are wrong:**
- A: Human approval contradicts "fully autonomous."
- B: No unsupervised training described.
- C: No database described.

**Key Concept:** Human-in-the-loop = AI recommends, human decides.

---

### Q13. A model outputs a probability (e.g., P(fraud) = 0.87) for each transaction, while another model writes a paragraph explaining the fraud case. Which pairing is correct?

A. First model = discriminative; second model = generative

B. First model = generative; second model = discriminative

C. Both are discriminative

D. Both are generative

**Correct Answer:** A

**Difficulty:** Moderate

**Topic:** Discriminative vs Generative

**Explanation:**
Predicting a probability/class from input is discriminative. Writing a free-form explanation produces new text, which is generative. Systems often pair a discriminator with a generator.

**Why the other options are wrong:**
- B: Reverses the assignment.
- C: The paragraph generator is not a classifier.
- D: The probability output is not generation.

**Key Concept:** Probability → discriminative; free-form text → generative.

---

### Q14. Which is a genuine limitation of Generative AI that a developer must design around?

A. Models always require an internet connection to run

B. Models do not inherently know what is true, so outputs must be validated

C. Models cannot process text longer than a sentence

D. Models cannot handle any ambiguity in input

**Correct Answer:** B

**Difficulty:** Moderate

**Topic:** Model Limitations

**Explanation:**
LLMs optimize likelihood of text, not truth. Correctness is not guaranteed by the generator itself — hence validation, retrieval, and human review. An internet connection, short-text limits, and total intolerance of ambiguity are not intrinsic limitations.

**Why the other options are wrong:**
- A: Models run offline; connectivity is deployment-specific.
- C: Models process very long texts.
- D: Models handle ambiguity poorly in nuanced cases but not 'not at all.'

**Key Concept:** Generation ≠ verified truth; always design validation.

---

### Q15. A bank wants an LLM to draft replies to customer complaints. What is MOST important at the output stage?

A. Making every reply as long as possible for thoroughness

B. Delivering replies without human review to cut cost

C. Verifying each reply for factual and regulatory accuracy before sending

D. Setting the highest possible randomness for creativity

**Correct Answer:** C

**Difficulty:** Moderate

**Topic:** Model Output / Human Oversight

**Explanation:**
In financial domains, an unsupported or inaccurate statement has real liability. The critical control is validating factual and regulatory soundness (ideally with a human) before a reply is sent. Length, cost-cutting, and maximum randomness are not the priority.

**Why the other options are wrong:**
- A: Length is not quality.
- B: Skipping review increases risk.
- D: High randomness reduces reliability.

**Key Concept:** High-stakes outputs require validation gates.

---

### Q16. A vendor demos a GenAI tool that answers brilliantly on the three sample queries shown. Why is it risky to conclude it will perform this well in production?

A. Demo inputs are usually representative of all real user queries

B. Production performance always matches demo performance

C. A good demo guarantees the model has been production-hardened

D. Demos often use cherry-picked inputs that do not reflect real-world distribution or edge cases

**Correct Answer:** D

**Difficulty:** Moderate

**Topic:** Evaluation / Distribution Mismatch

**Explanation:**
Vendors select favourable examples; real users write varied, ambiguous, adversarial inputs. Performance on a few curated prompts does not generalize, so a rigorous evaluation on your own data is needed before trusting the tool.

**Why the other options are wrong:**
- A: Real inputs are far more varied.
- B: Demos overstate typical production performance.
- C: Demos do not prove production hardening.

**Key Concept:** Evaluate on YOUR realistic data, not vendor demos.

---

### Q17. An LLM generates perfectly formatted citations, several of which reference papers that do not exist. Which mitigation is most appropriate?

A. Ground the answer in retrieved, verifiable sources and check each citation against them

B. Increase the temperature so the model is more 'careful'

C. Retrain the model from scratch every week

D. Increase the context window to 1 million tokens

**Correct Answer:** A

**Difficulty:** Moderate

**Topic:** Factual Verification / Hallucination Mitigation

**Explanation:**
Non-existent references are fabricated details. The reliable fix is grounding — retrieving from actual sources (e.g., RAG) and verifying citations, because temperature and context size do not add truth, and retraining is impractical.

**Why the other options are wrong:**
- B: Temperature changes randomness, not factual reliability.
- C: Impractical and unrelated.
- D: Context width does not authenticate references.

**Key Concept:** Verify generated facts against external sources.

---

### Q18. A legal team wants LLM summaries of contracts. What should the team do FIRST before deployment?

A. Deploy immediately; the model is clearly talented

B. Define evaluation criteria and test the pipeline on a sample of annotated contracts

C. Set temperature to maximum for fluent summaries

D. Assume the model already knows every jurisdiction's legal specifics

**Correct Answer:** B

**Difficulty:** Moderate

**Topic:** AI Output Validation / Evaluation-First

**Explanation:**
For any high-stakes model, the first step is defining correctness criteria and measuring performance on representative data. Evaluation drives prompt/data/architecture decisions; the rest occur later.

**Why the other options are wrong:**
- A: Shipping before evaluation is reckless.
- C: High temperature harms reliability.
- D: Models do not reliably hold domain specifics.

**Key Concept:** Evaluate first, deploy after.

---

### Q19. A company replaces its human spreadsheet checkers with an LLM asked to read tables and report totals. What is the biggest risk in this design?

A. LLMs always summarise numeric tables with perfect accuracy

B. The approach is technically impossible — LLMs cannot read tables

C. The LLM can hallucinate or misread numeric cells, so results must be cross-checked programmatically or by a human

D. Spreadsheets are not a supported input format for LLMs

**Correct Answer:** C

**Difficulty:** Hard

**Topic:** Model Limitations / Numeric Reliability

**Explanation:**
Tokenization and next-token prediction make exact numeric transcription/arithmetic unreliable. For anything audit-critical, outputs should be verified: either the model should call a calculation tool or a checker must independently recompute values.

**Why the other options are wrong:**
- A: Perfect arithmetic is not guaranteed.
- B: LLMs can process tabular text.
- D: Tables can be supplied as structured text.

**Key Concept:** LLMs are unreliable for exact numbers — use tools/checkers.

---

### Q20. Which problem is better suited to a traditional discriminative ML model than to a generative model?

A. Writing a poem about autumn

B. Translating a paragraph from French to English

C. Editing a sentence to sound more formal

D. Classifying emails as spam or not spam

**Correct Answer:** D

**Difficulty:** Hard

**Topic:** Discriminative vs Generative Choice

**Explanation:**
Spam classification is a binary decision on existing content — precisely a discriminative task where a classifier excels. Generation, translation, and style rewriting all produce new text and suit generative models.

**Why the other options are wrong:**
- A: Creative generation.
- B: Sequence-to-sequence generation.
- C: Text transformation/generation.

**Key Concept:** If the answer is a label, think discriminative; if it is new content, think generative.

---

### Q21. A model states a claim with 95% claimed confidence, yet the claim is factually wrong. What does model 'confidence' NOT guarantee?

A. Factual correctness

B. Fluent wording

C. Grammatical structure

D. Textual consistency with the surrounding paragraph

**Correct Answer:** A

**Difficulty:** Hard

**Topic:** Hallucination / Synthetic Confidence

**Explanation:**
A model's self-reported confidence reflects token probabilities, not verified truth. Fluency, grammar, and local coherence can all be high while the substance is wrong — which is exactly why confidence is not a validity signal.

**Why the other options are wrong:**
- B: Confidence correlates with fluent phrasing.
- C: Grammar can be perfect.
- D: In-paragraph consistency can hold.

**Key Concept:** Model confidence ≠ factual certainty.

---

### Q22. A GenAI tool answered perfectly on every question during the vendor's training demo but fails badly on the company's real users. What is the most likely cause?

A. The model is deterministic, so it should always perform identically

B. Distribution shift — real-world inputs differ from the curated demo data the model was showcased on

C. The temperature was changed by the users

D. Production users caused the model to relearn from scrap data

**Correct Answer:** B

**Difficulty:** Hard

**Topic:** Distribution Shift / Evaluation

**Explanation:**
Curated demos are a narrow slice of inputs; production traffic includes ambiguous phrasing, rare edges, and domain jargon. This mismatch ('distribution shift') is the standard explanation for demo-to-production performance collapse.

**Why the other options are wrong:**
- A: Determinism does not imply equal quality on different inputs.
- C: Temperature is not changed by users.
- D: Users do not retrain the model.

**Key Concept:** Test on production-like data to reveal distribution shift.

---

### Q23. A text-only LLM, never explicitly programmed for arithmetic, is able to solve addition problems at inference time. What is the best explanation?

A. A hidden rule-based arithmetic engine inside the model

B. Lightning-fast lookup against a stored answers table

C. Emergent capability: patterns and implicit reasoning learned from vast text during pretraining

D. It passively mirrors an internet connection

**Correct Answer:** C

**Difficulty:** Hard

**Topic:** Emergent Capabilities

**Explanation:**
Large-scale pretraining causes capabilities that were never explicitly coded — pattern-based computation emerges from the sheer volume of data and parameters. There is no internal arithmetic engine, no lookup table, and no default internet access.

**Why the other options are wrong:**
- A: Models contain no explicit symbolic calculator.
- B: No answers table is stored.
- D: Models do not browse by default.

**Key Concept:** Emergence = capability from scale, not from explicit rules.

---

### Q24. Which statement about Generative AI and training data is TRUE?

A. Generative models reliably produce 100% novel content and never reproduce training data

B. Generation involves no data at all

C. Generative models statistically reproduce the content distribution of their training data

D. Audio and image models cannot reproduce any training-like content

**Correct Answer:** C

**Difficulty:** Hard

**Topic:** Training Data / Memorization

**Explanation:**
Generative models learn the training distribution; when they memorise inputs (common repeated data), outputs can echo near-verbatim training content — a well-known privacy/copyright concern. 'Everything is novel' and 'no data involved' are both false myths.

**Why the other options are wrong:**
- A: Near-verbatim reproduction is possible for memorised data.
- B: Training is data-intensive.
- D: Audio/image models can reproduce memorised content too.

**Key Concept:** Generation models the training distribution and can memorise.

---

### Q25. A hospital deploys an LLM that drafts discharge summaries from patient records. Which practice is essential before go-live?

A. Human clinician review for every output plus a defined model-failure escalation path

B. No oversight, so the model can run at full speed

C. Relying solely on the model because it is expensive to supervise

D. Checking only that outputs are grammatical

**Correct Answer:** A

**Difficulty:** Hard

**Topic:** Human Oversight / AI Security

**Explanation:**
Drafting clinical documents touches patient safety. The essential control is clinician sign-off on every output, with escalation when the pipeline fails. Grammar checks alone are grossly insufficient.

**Why the other options are wrong:**
- B: Unreviewed medical text is unsafe.
- C: Cost does not remove the need for review.
- D: Clinical correctness far outweighs grammar.

**Key Concept:** In patient-facing systems, human sign-off is non-negotiable.

---

### Q26. A company wants an automated detector to flag AI-generated product images. What is the fundamental challenge?

A. No detection approach exists in any form

B. Detectors generalise poorly to new generators, so no current method is foolproof — verify with multiple signals

C. Detecting AI images is exactly as reliable as classifying cats versus dogs

D. AI images always contain visual labels

**Correct Answer:** B

**Difficulty:** Hard

**Topic:** AI Output Validation / Deepfakes

**Explanation:**
Generators improve constantly and detectors trained on one generator's patterns often fail on others. Combining methods (metadata, watermarks, detectors) reduces risk but nothing is 100% reliable, so claims of guaranteed detection are false.

**Why the other options are wrong:**
- A: Detectors exist; the issue is reliability.
- C: AI-image detection is far harder and generator-dependent.
- D: No visible label is required.

**Key Concept:** AI detection is probabilistic, not foolproof.

---

### Q27. A developer sets an LLM's temperature very high. What effect is expected on outputs?

A. Outputs become more deterministic and repetitive

B. Inference gets faster

C. Outputs become more random and can become incoherent or off-topic

D. The context window effectively doubles

**Correct Answer:** C

**Difficulty:** Hard

**Topic:** Temperature / Randomness

**Explanation:**
Higher temperature makes the model sample from flatter token distributions — more variety, more risk of incoherence and off-topic content. It changes sampling randomness, not speed, determinism, or context size.

**Why the other options are wrong:**
- A: That is the effect of very low temperature.
- B: Temperature does not affect compute speed.
- D: Context window is fixed by the model settings.

**Key Concept:** High temperature = more random output.

---

### Q28. A credit platform uses (1) an ML model that decides approve/reject and (2) an LLM that writes personalised denial letters. Which statement captures BOTH the category and the unique risk of each?

A. (1) is generative with bias risk; (2) is predictive with hallucination risk

B. Both are discriminative, so they share the same single risk

C. Both are unsupervised, so no validation is needed

D. (1) is predictive ML with bias-in-training-data risk; (2) is GenAI with risk of unsupported or inappropriate content

**Correct Answer:** D

**Difficulty:** Advanced

**Topic:** Multi-model Risk Analysis

**Explanation:**
A body of application for approving/rejecting is discrimination; its dominant risk is bias in the training data. Writing denial letters is generation; its risks are unsupported statements and tone. Correctly pairing systems with distinctive risks is exactly what a reviewer should do.

**Why the other options are wrong:**
- A: Reverses which system is generative.
- B: The two systems are not identical and have different risk profiles.
- C: Neither system is described as unsupervised.

**Key Concept:** Name the model type, then name its characteristic risk.

---

### Q29. A vendor claims their LLM is 'genuinely intelligent' because it answered 10 showcase prompts correctly. Why is this reasoning flawed?

A. Correct answers on a handful of curated prompts do not establish understanding, reasoning, or generalisation

B. Fluent text is sufficient proof of true intelligence

C. Fluency is the same thing as intelligence

D. Nailing showcase prompts proves AGI

**Correct Answer:** A

**Difficulty:** Advanced

**Topic:** Evaluating Intelligent-Looking Systems

**Explanation:**
Showcase prompts can be memorised or pattern-matched. Generalisation, robustness, and genuine reasoning require evaluation across diverse, adversarial, out-of-distribution tests, not a small favourable set. Fluency and intelligence are distinct.

**Why the other options are wrong:**
- B: Fluency can occur without understanding (stochastic parrots phenomenon).
- C: Fluency ≠ reasoning.
- D: AGI claims need far stronger evidence.

**Key Concept:** Small favourable samples cannot prove intelligence.

---

### Q30. An app predicts fraud (0/1) and then generates an English explanation for the decision. An audit finds explanations look correct but occasionally do not match the actual decision path. What is the most important audit insight?

A. Generated explanations are always faithful to the true mechanism

B. Because the LLM is large, its explanations are guaranteed accurate

C. Post-hoc generated explanations can be fluent yet unfaithful to the real prediction logic; the pipeline needs faithfulness monitoring

D. Explanations never matter in regulated settings

**Correct Answer:** C

**Difficulty:** Advanced

**Topic:** AI Output Validation / Explainability

**Explanation:**
Generated (post-hoc) explanations are optimised to be plausible, not to reflect the model's true internal reasoning. In regulated contexts you must monitor whether explanations are faithful to decisions; fluency is not fidelity.

**Why the other options are wrong:**
- A: Post-hoc explanations can diverge from true logic.
- B: Model size does not guarantee faithful explanations.
- D: Explanations are critical in regulated settings.

**Key Concept:** Plausible text ≠ accurate explanation of model behaviour.

---

# SECTION 2 — LLMs (20 Questions)

### Q1. In LLM terms, what is a 'token'?

A. A complete stored document

B. A model parameter

C. The smallest unit of text the model processes — often a subword or word fragment

D. A single embedding stored in the vector database

**Correct Answer:** C

**Difficulty:** Easy

**Topic:** Tokens

**Explanation:**
Tokenizers split text into smaller pieces (words, subwords, or characters). The vocab has a fixed size, and both prompts and outputs are measured in tokens, which drive context-window and billing limits.

**Why the other options are wrong:**
- A: Documents are split into many tokens.
- B: Parameters are weights, not text units.
- D: Embeddings are vectors, distinct from tokens.

**Key Concept:** Tokens are sub-word text units; the model 'thinks' in them.

---

### Q2. What does an LLM's "context window" refer to?

A. The model's knowledge stored permanently after training

B. The size of the training dataset

C. The total number of parameters in the model

D. The maximum number of tokens (input + output) the model can consider in one request

**Correct Answer:** D

**Difficulty:** Easy

**Topic:** Context Window

**Explanation:**
The context window is a per-request cap on how many tokens the model can attend to at once. It is not knowledge storage, training data size, or parameter count.

**Why the other options are wrong:**
- A: Knowledge comes from weights + provided context.
- B/C: Different concepts entirely.

**Key Concept:** Context window = working memory size of one request.

---

### Q3. Which statement about tokenization is most accurate?

A. Every token is always exactly one full word

B. Tokenization only applies to images

C. Tokens are always single characters

D. Subword tokenization means a word can be split into multiple tokens (e.g., 'unhappiness' → several tokens)

**Correct Answer:** D

**Difficulty:** Moderate

**Topic:** Tokens

**Explanation:**
Most tokenizers use subword algorithms so rare/compound words become multiple tokens while common words stay single tokens. Tokens are rarely whole sentences and rarely always single characters.

**Why the other options are wrong:**
- A: Subwords break whole-word equivalence.
- B: Tokenization is primarily text.
- C: Tokens can cover whole common words.

**Key Concept:** 1 word can be many tokens (and vice-versa).

---

### Q4. What role does 'training data' play in an LLM's behaviour?

A. It is supplied fresh with every user query

B. It is the historical data from which the model learned its statistical patterns

C. It is the user's chat history stored on disk

D. It is the same thing as the context window

**Correct Answer:** B

**Difficulty:** Easy

**Topic:** Training Data

**Explanation:**
Pretraining data shapes model weights. After training, the model does not query this data; the context window supplies per-request information instead. Chat history is neither the context window nor training data.

**Why the other options are wrong:**
- A: Fresh data is supplied at inference as context.
- C: Chat history is session state, not training data.
- D: Distinct concepts.

**Key Concept:** Training data shapes weights; context supplies per-query info.

---

### Q5. An API allows 4,000 context tokens. Your prompt uses 3,800 tokens and you need a 500-token answer. What happens?

A. The API happily generates 500 tokens beyond the window

B. The model automatically expands its context window

C. Generation will be truncated or error out because the required output does not fit within the remaining 200 tokens

D. The model drops its prompt to make room

**Correct Answer:** C

**Difficulty:** Moderate

**Topic:** Context Window Limits

**Explanation:**
Input and output share the window. 3800 + 500 > 4000, so the generation cannot complete within limits — the call fails or gets cut off. Providers do not silently expand windows.

**Why the other options are wrong:**
- A: The cap is enforced.
- B: No dynamic expansion happens.

**Key Concept:** Input + output must fit the context window.

---

### Q6. Which statement about a larger context window is TRUE?

A. It lets the model consider more text at once but does not guarantee it uses all of it accurately

B. It permanently increases the model's vocabulary

C. It reduces the number of training parameters

D. It guarantees perfect recall of every token placed inside it

**Correct Answer:** A

**Difficulty:** Moderate

**Topic:** Context Window vs Performance

**Explanation:**
A bigger window is capacity, not accuracy. Models can ignore or mishandle portions of long contexts (the 'lost in the middle' effect), so merely adding tokens does not ensure high-quality answers.

**Why the other options are wrong:**
- B: Vocabulary is set by the tokenizer.
- C: Parameters are fixed at training time.
- D: Long-context comprehension is imperfect.

**Key Concept:** Capacity ≠ accuracy.

---

### Q7. A user tells a bot an important fact early in a long conversation; later the bot flatly contradicts that fact. What is the best explanation?

A. The bot forgot it 'in the human sense' — long context handling is imperfect and newer/irrelevant tokens can dominate attention

B. The model was privately retrained during the conversation

C. The model fetched contradictory data from the internet at runtime

D. A database join went wrong in the chat service

**Correct Answer:** A

**Difficulty:** Moderate

**Topic:** Context Window / Attention Limits

**Explanation:**
Models don't have human memory; they attend over whatever is in the window. With long or noisy context, early or mid-context details can receive little attention or get squeezed out, causing apparent 'forgetting'.

**Why the other options are wrong:**
- B: No retraining happens mid-chat.
- C: No runtime browsing by default.
- D: Not a database operation.

**Key Concept:** The window is not memory; early details can be lost.

---

### Q8. A model has a knowledge cutoff of June 2024. A user asks about an event from March 2025. What can you reliably expect?

A. The model will always answer correctly because cutoffs don't matter

B. Ask anyway; the model will go online to learn about it

C. The model may have good recent knowledge because it updates nightly

D. The model has no reliable training-based knowledge of that event and must be given current sources in context to answer correctly

**Correct Answer:** D

**Difficulty:** Moderate

**Topic:** Knowledge Cutoff / Recency

**Explanation:**
A cutoff means training data ends at that date. Recent events must be supplied via retrieval/context; otherwise the model may guess or hallucinate. Models do not auto-update or browse by default.

**Why the other options are wrong:**
- A: Cutoffs materially limit recent knowledge.
- B: No default internet access.
- C: No nightly update of weights.

**Key Concept:** Post-cutoff information must be injected in context.

---

### Q9. A deployed assistant keeps answering with outdated product information. What is the immediate, most practical mitigation?

A. Retrain the whole model overnight

B. Increase temperature so answers vary less

C. Provide current information in the prompt via retrieval (e.g., RAG) so answers ground on fresh sources

D. Shorten all prompts to avoid confusion

**Correct Answer:** C

**Difficulty:** Moderate

**Topic:** Grounding Current Information

**Explanation:**
Injecting up-to-date context each request is fast and effective: the model grounds its answer in current sources without re-training. Retraining is slow/costly and shortening prompts does not fix outdated facts.

**Why the other options are wrong:**
- A: Impractical for frequent updates.
- B: Temperature is unrelated to freshness.
- D: Prompt length is not the issue.

**Key Concept:** Freshness comes from retrieval, not retraining.

---

### Q10. When do a few input-output examples in the prompt help the model most?

A. Always, regardless of task

B. When the task has a specific format or behaviour that is easier to demonstrate than describe

C. Never — examples only confuse models

D. Only when the examples are very long

**Correct Answer:** B

**Difficulty:** Moderate

**Topic:** Few-Shot Prompting

**Explanation:**
Demonstrating a target format/behaviour via a handful of examples often outperforms pure description, especially for unusual formats. It is not universally needed, and examples should be short, correct, and relevant.

**Why the other options are wrong:**
- A: Some tasks are better zero-shot.
- C: Examples usually help.
- D: Long examples waste context.

**Key Concept:** Few-shot examples teach by demonstration.

---

### Q11. Even a well-trained LLM sometimes answers simple arithmetic questions incorrectly. Why?

A. Because LLMs never see arithmetic in training

B. Because token-level autoregressive prediction is not a rule-based calculator

C. Because maths requires a GPU, which isn't available

D. Because the context window blocks numbers

**Correct Answer:** B

**Difficulty:** Moderate

**Topic:** Model Limitations / Arithmetic

**Explanation:**
Arithmetic requires exact symbolic computation, yet LLMs predict tokens probabilistically — so digit-level errors happen. Reliable systems route arithmetic to calculator/tool calls instead of letting the model guess.

**Why the other options are wrong:**
- A: Arithmetic is plentiful in training data (which contributes to the pattern, not the flaw).
- C: Not a hardware issue.
- D: Numbers fit in context fine.

**Key Concept:** For exact computation, use tools, not raw LLM probability.

---

### Q12. Which statement about an LLM's memory across chat sessions is TRUE?

A. LLMs are stateless: each request stands alone unless the application persists and re-injects context

B. The model remembers all users' conversations permanently in its weights

C. Chat sessions always write into training data automatically

D. The model stores every session in a relational database by default

**Correct Answer:** A

**Difficulty:** Moderate

**Topic:** Statelessness / Memory

**Explanation:**
A bare LLM has no session memory; the app must pass prior turns back in the prompt, or store summaries elsewhere, to simulate memory. Nothing is silently written to weights or stored databases.

**Why the other options are wrong:**
- B/C: No automatic persistence into weights/training.
- D: No default database.

**Key Concept:** Memory is engineered via context, not native.

---

### Q13. After a follow-up question, a bot answers as if it never saw your earlier clarification. What is the most accurate technical explanation?

A. The model's weights 'forgot' the clarification

B. The clarification was removed from the stored training data

C. The clarification was no longer in the active context (dropped or de-emphasised), and the model only works with what is in context

D. The bot uses a memory chip that overflowed

**Correct Answer:** C

**Difficulty:** Hard

**Topic:** Context vs Model Memory

**Explanation:**
Multi-turn apps keep only recent/selected turns in context. If the earlier clarification fell out of scope, the model literally has no access to it — it's not a human-style forgetfulness, just an absence of the tokens in the working window.

**Why the other options are wrong:**
- A: Weights are static between requests.
- B: Training data is not user-specific.
- D: No such hardware concept.

**Key Concept:** If it's not in context, the model cannot use it.

---

### Q14. Which statement about long-context LLM usage is FALSE?

A. Performance on content buried in the middle of a very long context can degrade

B. Retrieval helps surface the most relevant passages regardless of their original position

C. Models can process context far longer than typical prompts

D. Placing key facts in the middle of a huge context guarantees they are perfectly used

**Correct Answer:** D

**Difficulty:** Hard

**Topic:** Context Window Limits

**Explanation:**
The 'lost in the middle' finding shows mid-context content is often handled worse than content near the start/end. So stashing key facts mid-document does NOT guarantee performance — A/B/C are all accurate statements.

**Why the other options are wrong:**
- A: This is a real, documented effect.
- B: Retrieval (RAG) is precisely a common remedy.
- C: True — long contexts are supported.

**Key Concept:** Place/reinforce key facts where the model attends best.

---

### Q15. A user says the bot's answer came 'from its brain' because the bot is confident. What correction should you give?

A. The bot bases answers only on its trained weights plus whatever is in the current context — there is no internal smooth-talking magically authoritative store

B. The bot updates its weights with every chat

C. The bot stores every answer in a hidden memory permanently

D. The bot saves its thoughts to a default SQL database

**Correct Answer:** A

**Difficulty:** Hard

**Topic:** Context vs Training

**Explanation:**
Confidence comes from token probabilities, not from retrieving a verified mental encyclopedia. Weighted statistics + provided context are the entire information budget. There is no hidden permanent memory.

**Why the other options are wrong:**
- B: Weights are not updated at inference.
- C: No hidden memory store.
- D: No default database.

**Key Concept:** Confidence ≠ access to a global truth store.

---

### Q16. Which statement about the temperature parameter is FALSE?

A. Lower temperature makes outputs more deterministic

B. Higher temperature increases output diversity

C. Temperature changes how many parameters the model has

D. Low temperature is common for factual/structured tasks

**Correct Answer:** C

**Difficulty:** Hard

**Topic:** Temperature

**Explanation:**
Temperature alters the sampling distribution at inference time. It has nothing to do with parameter count (fixed after training) or context size — those are separate settings.

**Why the other options are wrong:**
- A/B/D: All are accurate properties of temperature.

**Key Concept:** Temperature controls randomness of sampling, not model architecture.

---

### Q17. At each generation step, what does an LLM actually compute?

A. The entire final answer in a single shot

B. A random word chosen without any probability

C. A probability distribution over the next token, from which it samples (or takes the argmax)

D. An image embedding of the answer

**Correct Answer:** C

**Difficulty:** Hard

**Topic:** Autoregressive Generation Mechanics

**Explanation:**
The final token layer produces a probability across the vocabulary; the decoder then samples from it (temperature/argmax decide the pick), and that token feeds the next step. That loop is what 'generation' means.

**Why the other options are wrong:**
- A: Generation is step-by-step, not single-shot.
- B: Outputs are probabilistic, not random without distribution.
- D: Text generation does not produce an image embedding.

**Key Concept:** Each step = softmax over vocabulary → sample next token.

---

### Q18. A travel assistant must remember a customer's dietary preferences across many future visits. What is the best design?

A. Store a per-user preference summary and inject it into the context of each new session

B. Hope the base model remembers it across sessions

C. Re-train the entire model with that single user's chats

D. Keep increasing the context window until it holds all users' data

**Correct Answer:** A

**Difficulty:** Advanced

**Topic:** Persistent Memory via Context

**Explanation:**
Since bare LLMs are stateless, durable memory is built by persisting a compact user profile and injecting it at the start of each session. Retraining for one user is absurd; bigger context is global, not per-user.

**Why the other options are wrong:**
- B: No cross-session memory.
- C: Impractical and not per-request.
- D: Context windows are shared capacity, not per-user memory.

**Key Concept:** Build memory with persisted context, not model changes.

---

### Q19. Why can you not reliably extract exact sensitive training documents by simply asking an LLM to 'output your training file X'?

A. Because output is a sample from learned distributions/patterns, not an index into the original corpus

B. Because the model encrypts its training data

C. Because training data is stored in an unreachable cloud vault

D. Because training data is deleted as soon as training ends

**Correct Answer:** A

**Difficulty:** Advanced

**Topic:** Training Data & Memorization

**Explanation:**
The model stores compressed statistical patterns, not filenames or a retrieval index. It can regurgitate heavily-memorised fragments, but it cannot 'locate and print' arbitrary source files the way a search engine can.

**Why the other options are wrong:**
- B/C/D: No encryption, vault, or guaranteed deletion explains this.

**Key Concept:** LLMs are pattern samplers, not document indexes.

---

### Q20. A model correctly answers a niche question using an obscure 2010 fact, despite a 2023 cutoff. What is the correct conclusion?

A. This proves the model is online

B. This is impossible — models cannot know pre-cutoff facts

C. Pre-cutoff training data can absolutely cover that fact, but you still cannot verify its provenance — check/ground before trusting in high-stakes use

D. The model must have memorised it perfectly, so it is always correct

**Correct Answer:** C

**Difficulty:** Advanced

**Topic:** Knowledge Cutoff & Verification

**Explanation:**
A cutoff does not mean 'knows nothing before it' — older facts are part of training data. But a fluent correct-sounding answer is not proof the model is grounded; verification against sources is still required for important claims.

**Why the other options are wrong:**
- A: Correct answer ≠ online access.
- B: Pre-cutoff facts are exactly what the model does know.
- D: Memorisation is not verified truth.

**Key Concept:** Cutoff bounds recency, not recall accuracy; verify anyway.