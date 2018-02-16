# Cawsey, A. (1998). _The essence of artificial intelligence._ New York, NY: Prentice Hall.
## 1. Introduction
### Hits
- the overview of AI problems, including NLP and vision, search and planning, and expert systems
- knowledge representation, and that solving "even apparently simple problems requires lots of knowledge" and example of trying to interpret a newspaper headline knowing _only_ the meaning of words in a dictionary. without broader knowledge of current affairs, it would have meaning, but would not be meaningful
- philosophical issues, like Turing's Test and Searle's Chinese Room. the Chinese Room analogy, that computers are like a person in a room that has access to a Chinese dictionary and so appears to know Chinese but actually looks everything up, is interesting.

### Misses
- discussion of AI, that it is concerned with problem-solving that cannot be automated, like face recognition, felt circular: once AI is capable of facial recognition, it *could* be automated. so saying that AI is about non-automated problem-solving divides problems into "things we have figured out how to automate" and "things we haven't yet figured out how to automate"

## 2. Knowledge Representation and Inference
### Hits
- had no idea that logic was crucial in AI
- representational adequacy, how well a language can model the world, and inferential adequacy, how well the models can be used for predictions
- inferential efficiency: how costly an inference is
- clarity of syntax and semantics: how straightforward a language is to work with
- naturalness: natural language is expressive and efficient, but complex, so knowledge representation should be able to use natural language to some extent
- semantic networks and frames are essentially equivalent
  - class and subclass relationship;
  - inheritance
  - reasoning is restricted - just property inheritance and object relations - but intuitive and clear
  - frame: object is a frame, links represented with slots
- logic
  - propositional:
    - P & Q => R
    - !R => !(P & Q)
  - FOL
    - propositions, + constants, variables & functions
  - proof theory: what can be inferred from a set of propositions
- frames can be transformed into FOL, but not everything in FOL can be translated into frames. frames have weaker representational adequacy
- rule-based systems use condition-action statements to produce an action
  - forward-chaining: facts held in working memory as system acts and new facts are generated
    - recognize-act cycle: given conditions, find rules for those conditions. then execute rules. check conditions, and find rules for those conditions
  - backward-chaining: start with a goal. look for facts that satisfy that goal. if none, look for rules whose conclusions would satisfy the goal. try to prove the preconditions of that rule.
    - more efficient than forward-chaining when goal, or hypothesis, is known, because forward-chaining would produce irrelevant conclusions given the goal.

### Misses
- Russell & Norvig explain FOL more succinctly: FOL is propositional logic + objects and relations. Cawsey discusses constants, variables, and predicates.

## 3. Expert Systems
### Hits
- components of an expert system:
  - knowledge base ("KB"): declarative representation, predominantly FOL
  - inference engine
  - explanation system
- expert systems can be useful in deterministic and probabilistic circumstances. the former uses simple IF-THEN rules or certainty factors, the latter Bayesian networks
- knowledge engineering is intensive, and involves interviewing experts to determine how to formalize their reasoning so that an expert system can be developed
- even successful expert systems are not implemented, because solving the AI problem only addresses part of peoples' resistance to them
- Bayesian networks treat variables as _conditionally independent_, so if they actually tend to occur together, the network in its simplest form will _overestimate_ the likelihood of a disease
  - P(H | E) = P(H & E)/P(E)

### Misses
- that expert systems are useful when the benefits outweigh the costs is a conclusion that doesn't provide enough insight about the tradeoffs in using an expert system

## 4. Using Search in Problem Solving
### Hits
- generally, search is a fascinating concept
- state space is a graph, and search algorithm is set of rules for traversing the graph until a goal is met
- breadth and depth first search
  - depth first: search to dead end, then back track
  - breadth first: try every path at length 1, then length 2, length 3
- heuristic search:
  - A*
  - hill climbing: move to next_node iff BetterThan(next_node, current_node). halts when reaches a _local maxima_
  - best first: priority queue to try best first options, but eventually tries all options
- problem solving as search: state space, agenda, and a way to decide if the goal is reached or to keep going
- planning
  - means-end analysis: find an operator that minimizes the difference between the current and goal states
  - minimax procedure: state space for which one player minimizes, other player maximizes, and node values calculated accordingly
  - alpha-beta pruning: compares the best case of a maximizing node, alpha, with the worst case of a minimizing node, beta. since alpha is the floor of the best outcomes, and beta the ceiling of worst case outcomes. if beta < alpha, tree is 'pruned' of that branch

### Misses
- seeing more of the math would have been interesting. the conceptual presentation is great, but having some of the mathematics underlying it would have been a foundation for further exploration

## 5. Natural Language Processing
### Hits
- speech recognition is part of the challenge. how can a system properly identify words from a continuous stream of sound?
- natural language cannot be rewritten, so NLP is a search problem. that is, the state space is immutable, so goal is to traverse it
- syntax (structure of sentence, given rules) and semantics (meaning, given syntax). with pragmatics, have concept of context. what does 'that' refer to in a sentence?
  - each can be ambiguous.
  - syntax: parse tree, creating a tree where nodes are syntactic structures - noun_phrase, verb_phrase, det, rel_clause, rel_pn, noun, verb, prep, prep_phrase
  - semantics:
  - compositional semantics: representing meaning of sentence with meaning of its parts
    - represent meaning with FOL
  - pragmatics:
    - plan recognition

### Misses
- apparently there is an alternative to a definite clause grammar which conflates syntactic and semantic analysis. obviously that's it's own chapter, but a quick discussion of why one wouldn't, or would, use that alternative would have been useful.


## 6. Vision
### Hits
- there is no simple mapping from a visual signal to a recognized object
- steps:
  - pixel and edge recognition
    - average pixel intensity "smooths" an image, removing the "noise" of, say, texture so that a vision system can focus on larger objects
  - edges that form regions with orientations
    - calculate amount of difference in pixel brightness; difference of a certain size = edge
  - three dimensional grouping of oriented regions
    - stereopsis is based on trigonometry, but requires determining image correspondence: what point in an image perceived through one eye corresponds to what point in the image perceived by the other eye
- to recognize an object, we need a model of that object, e.g. volumetric primitives. object recognition is very knowledge intensive
- practical vision systems could use alternatives to human vision, e.g. sonar
- active vision, which is the human ability to center an object of interest in the visual field by moving the head, body and eyes, is useful in computer vision - allowing the visual processing system to move the camera

### Misses
- if sonar is an alternative (or a complement? this wasn't clear), why not use it more often?
- good job of discussing the complexity of vision. but what about humans makes us powerful visual processors (this has to do with the large areas, V1-V5, devoted to vision processing in our brains. discussing this, or its implications for AI, would have been interesting)

## 7. Machine Learning and Neural Networks
### Hits
- inductive learning: training a system to induce a rule, given examples. particularly used in classification tasks: here are a bunch of cat pictures, induce a cat model
- version space learning: treat rule as a conjunction of facts
  - what are the features?
  - what are their values?
- candidate selection algorithm: basic idea is to have a specific set and a general set, and to connect them by adding or removing features. but overall this section of the chapter was difficult to follow
- decision-tree induction:
  - ID3 algorithm uses classification and regression trees.
- genetic algorithms
  - takes idea of randomness and competition in evolution. create some set of possible solutions. combine the solutions, score the outcomes, score the best sets, combine them
    - add in a mutation function, to create some randomness and explore the solution space beyond what combinations of the best solutions would cover
- neural networks
  - create 'neurons', and the interaction of many neurons can create complex results.
  - sub-symbolic. there is no 'symbol' representation. instead, there are neuron outputs, and weights on neuron connections. if threshold on weights reached, neurons fire together
  - neural nets are useful for pattern recognition
  - more complex networks use input units, hidden units, and output units, connected by weighted connections. this is a "two-layer" network. the input layer of units just distributes values to the hidden layer, which passes information to the output layer
  - backpropagation gives a value on [0, 1] rather than binary output 0 or 1. thus adjusts weights more or less depending on closeness to correct rule

### Misses
- the discussion of the candidate elimination algorithm was recondite. the idea was there, and was very interesting. but the exposition was opaque.
- too often throws in "anyway" as a transition.

## 8. Agents and Robots
### Hits
- clear definitions
  - "an intelligent agent can act independently with well-defined goals"
  - "a robot perceives and manipulates objects in the environment"
- classic AI approach, symbolic representation and reasoning, used in robots. but new approach is to implement primitive behaviors, and enable robot to respond directly to environment
- manufacturing robots are more engineering and organizational challenges than AI challenges.
- agent-oriented programming: specialized languages and knowledge representation to design agents that communicate with each other
- email agents: expert system, using NLP and adjusting responses based on machine learning
- autonomous robots use and have motivated progress in AI because environments are dynamic, so need to handle uncertainty without having a programmed list of all possible circumstances

### Misses
- agents are a great topic for introducing cognitive architectures, e.g. Shakey the robot. but Cawsey doesn't present them, and so the examples are interesting but the chapter remains too summary



## Chong, H., Tan, A. & Ng, G. (2007). Integrated cognitive architectures: A survey. *Artificial Intelligence Review 28*, 103-130.
### Summary
- an **integrated cognitive architecture** is "a single system... capable of producing all aspects of human behaviour... across various domains and knowledge bases"
- ICAs draw on AI, cognitive psych, and neurobiology
- State, Operator, and Result (SOAR) ACT-R, and ICARUS symbolic representation, production-rule-based inference, means-end analysis for problem solving. But, ACT-R and ICARUS are based on psychological cognitive architectures
- Belief-Desires-Intentions (BDI): primarily focused on agent's _commitments_ to plans of action
- Subsumption: behavior-based, and has no learning or problem solving module. higher layers _subsume_ lower layers, much as in neurobiological models
- CLARION: symbolic + neural nets; like ACT-R, uses AI, cognitive psych, and neurobiology concepts

### Interesting Architectures
- SOAR
  - LT + W memory
  - 5-phase decision cycle: input, elaboration, decision, application, output
  - learns from procedural 'impasses' (halts) by chunking (pattern creation), reinforcement; episodic and semantic store additional cues
  - goals: working memory, goal-subgoal hierarchy
  - problem solving: decision procedures to select operators; means-end analysis
  - planning: decision cycle + actions => closer to goal state
- ACT-R
  - modules: visual, manual, declarative, goal. coordinated through the central production system, equivalent to the basal ganglia
  - goals: stored in intentional module, available through goal buffer
  - problem-solving: chunks activated in Bayesian framework, production rule that matches chunk fires
  - planning: creating subgoals
- Connectionist learning with adaptive rule induction on-line (CLARION)
  - procedural in neural nets + declarative for novel situations
  - neural, symbolic and reinforcement learning for "on-line, bottom-up learning"
  - uses a declarative, rule based system and procedural, "subsymbolic neural mechanisms"
    - explicit learning is rule-based; implicit learning is by reinforcement learning with multilayer neural networks and back-propagation algorithms
  - goals: goal structures like goal lists and queues
  - problem solving: Q-values (neural nets) + declarative rules
  - planning: "beam search in the Q-value space" -> pick actions and sequence to maximize probability of goal achievement

### Insights
- all architectures surveyed used working memory (in some form), production rules and a decision process
- most architectures distinguish declarative and procedural knowledge
- architectures that include different kinds of memory, e.g. episodic, are more complex and more human-like

### Issues
- reviews each architecture thoroughly, but doesn't compare them; for example, many use the Tower of Hanoi as a test, but the article doesn't discuss how each performs on that test or what distinguishes their approaches to it


## Nilsson, N. J. (2010). *The quest for artificial intelligence.*
### Summary
Chapter 31: Intelligent System Architectures
**Computational Architectures**
- von Neumann architecture: main program, subprograms. Main program calls subprogram-1, which calls subprogram1-1, which calls subprogram1-1-4. they run recursively, returning control to the calling program until the main program receives control. Interrupts enable a system to watch for special conditions and transfer control to the relevant program immediately (p. 561).
  - early AI programs used this
  - can use parallel processing or simulate parallel processing via time-sharing
- three-layer architecture: (1) reactive control algorithms which map sensors directly onto actuators with little or no internal state; (2) algorithms for governing routine sequences of activity that rely on internal state but perform no search; (3) search-based algorithms, such as planners
- "behavior-based" ("subsumption"): specific behaviors that robot executes depending on environmental stimuli; can result in "emergent behavior", e.g. flocking
- Beliefs, desires, intentions: beliefs := knowledge of environment in first-order predicate calculus; can change. desires := goals. intentions := goals the agent has begun a plan to achieve.
  - Procedural Reasoning System, a specific BDI architecture:
    - database of current beliefs, about the environment and itself, and agent's subject areas. some initially installed, others generated through perceptual apparatus and inference mechanisms. represented in first-order predicate calculus
    - goals are conditions to satisfy, internal and external
    - KA (knowledge areas): each KA is a specific procedure specifying a plan to accomplish a task, such as picking up an object. each KA has a body, the steps, and the condition under which it is executed. a "primitive" KA could be an action directly performable by the system, and so have no body
    - intention: KA and all sub-KAs to run
    - interpreter runs the system, including changing the intention based on changing environment
  - multi-agent communication: Knowledge Query Manipulation Language, which uses Knowledge Interchange Format, a language based on first-order predicate calculus.
    - A to B: (ask if (> (size chip1) (size chip2)))
    - B to A: (reply true)
    - B to A: (inform (= (size chip1) 20))

**Cognitive Architectures**
A cognitive architecture is "the basis for wide-ranging investigations into basic intelligent capabilities - such as problem solving, planning, learning, knowledge representation, natural language, perception and robotics - as well as applications in areas such as expert systems and psychological modeling." Paul S. Rosenbloom, in QAI, p. 578.
- Production Systems: based on extensive experimental work with human subjects performing problem-solving tasks.
  - Productions - IF-THEN rules, where IF = a condition, and THEN = an action - Long Term Memory + Working Memory, when condition parts of rule match data in WM, action executes, which writes or erases data in WM or takes action in the external environment. when data in WM changes, new rules execute.
  - Conflict Resolver decides which action or actions execute when > 1 could execute
  - Perception writes data on the environment to WM
- ACT-R (Adaptive Control of Thought - Rational):
  - Modules. Motor Module acts on the environment; other modules, including visual, Declarative Memory, Procedural Memory.
  - Buffers: interfaces between modules
  - Pattern Matcher: looks for a production that matches the current state of the buffers; production can modify buffers
- SOAR (States, Operator And Result): "tightly coupled hierarchy of layers - memory, decision and goal - in which each layer forms the inner loop of the layer above it. These layers increase progressively in both complexity and time scale from the bottom to the top" layer.
  - problem space: current state + operators available. SOAR sets up subsidiary problem spaces. this is "universal subgoaling", and can result in a "deep tree of subgoals and problem spaces". can invoke "weak" methods: hill climbing, means-end analysis, heuristic search

### Insights
- cognitive architecture models, both 'computational' and 'psychological'
- cognitive architecture diagrams
- connections with other AI systems

### Issues
- some treatment is not sufficiently deep, as this is a survey (of cognitive architectures, and generally of the field of AI)

## Latham, A., Crockett, K. & McLean, D. (2014). An adaptation algorithm for an intelligent natural language tutoring system. *Computers & Education 71*, 97-110.
### Summary
- intelligent tutoring system --> conversational ITS as complexity of interfaces (including menus and hyperlinks) has increased
- the Oscar CITS has a modular architecture that separates the domain and learning styles from the functionality
- architecture includes a controller, GUI, learning styles predictor, learning styles adapter, student model, and conversational agent
- Oscar CITS predicts and individual's preferred learning style through behavior and dialogue in conversation
- of the two methods (semantic-based and pattern matching), text-based CAs generally use pattern matching, because it is the most flexible for extended dialogues.
- pattern matching CAs match key words and phrases to a knowledge base of stimulus-response pairs (a script). but developing the script can be arduous

### Insights
- extended dialogue in CA calls for pattern matching
- pseudocode for adaptation algorithm
- interesting take on how a CA could teach a user, e.g. helping someone learn how to use a new word or concept or method

### Issues
- more focused on the CITS than the actual CA

## Bohus, D. & Rudnicky, A.I. (2009). The RavenClaw dialog management framework: Architecture and systems. *Computer Speech and Language 23*, 332-361.

### Summary
A dialog manager maintains a conversation history and interprets input. In conversation, the dialog manager must manage uncertainty about the semantics of input, and recover from errors in deciding what the most likely is. Additionally, the dialog manager must handle conversational phrases, like "what was that?", "wait a second", and "hang on" (p. 334).

Current approaches to dialog management: "finite-state, form-filling, information-state-update, plan-based" (p. 334).

### Insights
- excellent summary of finite-state, form-filling, information-state-update, and plan-based dialog management
- by decoupling domain-specific dialog and general dialog, RavenClaw enables broader input into the general dialog function and reuse of it across CAs
- RavenClaw provides "detailed information" about its sub-components, states and decisions, including computations

### Issues
- limited description of competing architectures


## Tsai, T.J., Stolcke, A, & Slaney, M. (2015). A study of multimodal addressee detection in human-human-computer interaction. *IEEE Transactions on Multimedia 17*(9), 1550-1561.
### Summary
"Addressee Detection" is the function that determines who a person is communicating with. The function incorporates a variety of inputs in the human-human context. Human-computer dialogues are simpler contexts and enable system designers to base interactions on simple rules. But in the human-human-computer context, old methods (push-to-talk, prompted interaction) are no longer sufficient because of the complexity of dialogue and the extent of the interaction domain, e.g. a person might stop a conversation thread with a human and prompt the computer to "find a recipe for dinner".

In multi-party communication with robots present, humans tend to gaze at the party they are addressing. Further, how a person communicates with a computer depends on how the person views the role of a computer, i.e. whether as a kiosk or receptionist. Finally, humans use "lexical, gaze, and prosodic" information when communicating among themselves to determine the addressee.

### Insights
- the computing cost of addressee detection is moderated by the reuse of information that a dialogue system must compute already, including ASR
- speakers change their speaking styles according to whom they are talking to
- acoustic energy was a feature that signaled a person was speaking to the computer; however, as conversational agents become more human-like in interaction, this acoustic energy variance will likely diminish as humans speak more naturally with the CA

### Issues
- interesting technical study and details, but lacked a hypothesis - e.g., what would be the model that suggests including all of the 'features' they tested?


## Kumar, R. & Rose, C. (2011). Architecture for building conversational agents that support collaborative learning. *IEEE Transactions on Learning Technologies 4*(1), 21-34.
### Summary
Conversational Agents ("CAs") have been used as tutors in reading and foreign languages to algebra, calculus, and physics. The value of CAs in learning is the dynamic scaffolding they provide. But traditionally, the interaction has been one-to-one, with one CA working with one learner.

In one-to-one interactions, state-based and plan-based interactions are supported. But in group settings, these approaches are less effective. In plan-based interactions, which are "flexible and robust", tremendous effort is required to model the CA's goals, the operators it has available, possible steps, and preconditions that the planning algorithm requires.

There are two assumptions in one-to-one interactions: each party, the person and the CA, will take turns; and, the addressee is the person who is not the speaker. Both assumptions are unavailable. There is no assumption that a response in the multi-party setting is an answer to the CA's question. (Even in the one-to-one setting, this issue arises but sophisticated solutions have proved effective).

A problem with, e.g., the Ravenclaw architecture is that it "processes user utterances only when the agent... is expecting input" (p. 27). But Basilica uses a separate, dedicated "component" to detect interaction changes, like a student's become inactive. Further, it uses a tutoring system that, at certain points, bars input.

### Insights
- List of components - e.g. *Listeners*, *Actors*, *Filters* - that Basilica CA architecture uses
- the Attention Grabbing and Ask When Ready strategy to present relevant information to a group conversation based on what the CA heard and interpreted
- elements of object-oriented software development applied to CA development

### Issues
- it's not clear how exactly a Basilica CA overcomes the problem of not knowing when a group conversation is generating questions for it, and of knowing how to gather more information
