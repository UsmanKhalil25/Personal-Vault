### Rules of Inference
![[phpjtM6om.png]]
- Implication Elimination: A->B = ~AvB
- Bi-conditional Elimination: A<->B  = (A->B) and (B->A)
- De-Morgan's Law: ~(A and B) = ~A or ~B and vice versa
- Distributive Property: (A and (B or C)) = (A and B) or (A and C)
### Rules of Inference for Quantified Statements
![[e434bbcfe43ad43772d119cf277fba071.png]]


#### Knowledge based agents
- agents that reason by operating on internal representations of knowledge

	What does “reasoning based on knowledge to draw a conclusion” mean?
	Let’s start answering this with a Harry Potter example. Consider the following sentences:
	
	1.  If it didn’t rain, Harry visited Hagrid today.
	2.  Harry visited Hagrid or Dumbledore today, but not both.
	3.  Harry visited Dumbledore today.
	
	Based on these three sentences, we can answer the question “did it rain today?”, even though none of the individual sentences tells us anything about whether it is raining today. Here is how we can go about it: looking at sentence 3, we know that Harry visited Dumbledore. Looking at sentence 2, we know that Harry visited either Dumbledore or Hagrid, and thus we can conclude
	
	4.  Harry did not visit Hagrid.
	
	Now, looking at sentence 1, we understand that if it didn’t rain, Harry would have visited Hagrid. However, knowing sentence 4, we know that this is not the case. Therefore, we can conclude
	
	5.  It rained today.
	
	To come to this conclusion, we used logic, and today’s lecture explores how AI can use logic to reach to new conclusions based on existing information.

#### Sentence (in AI)
- an assertion about the world in a knowledge representation language

#### Proposition Symbols
- P
- Q
- R
#### Logical Connectives
- not 
- and 
- or
- implication
	- if p is false then we can make no claim, -> will be true
	- if both are same then true, otherwise the second one
- biconditional
	- if both are same then true
	 Go through article 1.1 for the truth tables of logical connectives

#### Model
- assignment of a truth value of every propositional symbol ("a possible world")
- For example, if P: “It is raining.” and Q: “It is Tuesday.”, a model could be the following truth-value assignment: {P = True, Q = False}. This model means that it is raining, but it is not Tuesday. However, there are more possible models in this situation (for example, {P = True, Q = True}, where it is both raining an a Tuesday). In fact, the number of possible models is 2 to the power of the number of propositions. In this case, we had 2 propositions, so 2²=4 possible models.
#### Knowledge base
- a set of sentences know by a knowledge-based agent
- The knowledge base is a set of sentences known by a knowledge-based agent. This is knowledge that the AI is provided about the world in the form of propositional logic sentences that can be used to make additional inferences about the world.
#### Entailment(⊨)
- If α ⊨ β (α entails β), then in any world where α is true, β is true, too.
- For example, if α: “It is a Tuesday in January” and β: “It is January,” then we know that α ⊨ β. If it is true that it is a Tuesday in January, we also know that it is January. Entailment is different from implication. Implication is a logical connective between two propositions. Entailment, on the other hand, is a relation that means that if all the information in α is true, then all the information in β is true.

#### Inference
- driving new sentences from old ones
#### Model Checking
- To determine if KB ⊨ α:
	- Enumerate all possible models
	- If in every model where KB is true, α is true, then KB entails α
	- whenever our knowledge (what we know ) is true, then we check α must also be true
	- ![[Screenshot from 2024-01-31 23-15-21.png]]

#### Knowledge Engineering
- Knowledge engineering is the process of figuring out how to represent propositions and logic in AI.
#### Clue
- We put one of the cards from each category inside the envelop and try to determine the three cards inside the envelop
- Propositional Symbols
	- Note that each propositional symbol can be either true or false
	- People
		- Mustard
		- Plum
		- Scarlet
	- Room
		- Ballroom
		- Kitchen
		- Library
	- Weapon
		- Knife
		- revolver
		- wrench
- Knowledge
	- We know that at least one card of each category in present in the envelop
	- (mustard or plum or scarlet)
	- (ballroom or kitchen or library)
	- (knife or revolver or wrench)

#### Logical Puzzles
- Gilderoy, Minerva, Pomona and Horace each belong to a different one of the four houses: Gryffindor, Hufflepuff, Ravenclaw and Slytherin House
- Gilderoy belongs to Gryffindor or Ravenclaw
- Pomona does not belong in Slytherin
- Minerva belongs to Gryffindor
- Note that the solution is from inspection:
	- Minerva is in Gryffindor
	- Gilderoy is in Ravenclaw
	- Pomona is in Hufflepuff
	- Horace is in Slytherin
- To solve the problem logically we want to form 16 propositional symbols of form XY, where X is person name and Y is house name
	- for example: MinervaGryffindor, GilderoyHufflepuff and 14 more
- Check the puzzle.py for more clarity on how to encode the logic for it

#### Mastermind

Another type of puzzle that can be solved using propositional logic is a Mastermind game. In this game, player one arranges colors in a certain order, and then player two has to guess this order. Each turn, player two makes a guess, and player one gives back a number, indicating how many colors player two got right. Let’s simulate a game with four colors. Suppose player two suggests the following ordering:

![Mastermind1](https://cs50.harvard.edu/ai/2024/notes/1/mastermind1.png)

Player one answers “two.” Thus we know that some two of the colors are in the correct position, and the other two are in the wrong place. Based on this information, player two tries to switch the locations of two colors.

![Mastermind2](https://cs50.harvard.edu/ai/2024/notes/1/mastermind2.png)

Now player one answers “zero.” Thus, player two knows that the switched colors were in the right location initially, which means the untouched two colors were in the wrong location. Player two switches them.

![Mastermind3](https://cs50.harvard.edu/ai/2024/notes/1/mastermind3.png)

Player one says “four” and the game is over.

Representing this in propositional logic would require us to have (number of colors)² atomic propositions. So, in the case of four colors, we would have the propositions red0, red1, red2, red3, blue0… standing for color and position. The next step would be representing the rules of the game in propositional logic (that there is only one color in each position and no colors repeat) and adding them to the KB. The final step would be adding all the cues that we have to the KB. In our case, we would add that, in the first guess, two positions were wrong and two were right, and in the second guess, none was right. Using this knowledge, a Model Checking algorithm can give us the solution to the puzzle.

#### Theorem Proving
- initial state: starting knowledge base
- actions: inference rules
- transition model: new knowledge base after inference
- goal test: check statement we are trying to prove
- path cost function: number of steps in proof

#### Clause
- a disjunction of literals
	- P v Q v R

#### Conjunctive normal form
- logical sentence that is a conjunction of clauses
	- (A v B v C) and (D v ~E) and (F v G)


#### Conversion to CNF(conjunctive normal form)
- Elimination of biconditionals
	- turn (a<->b) into (a->b) and (b->a)
- Elimination of implications
	- turn (a->b) into ~a v b
- Move ~inwards using De Morgan's Law
	- turn ~(a and b) into ~a v ~b
- Use distributive law to distribute v wherever possible
	- move the v inwards and and outwards
-  Here’s an example of converting (P ∨ Q) → R to Conjunctive Normal Form: 
	-   (P ∨ Q) → R
	-   ¬(P ∨ Q) ∨ R /Eliminate implication
	-   (¬P ∧ ¬Q) ∨ R /De Morgan’s Law
	-   (¬P ∨ R) ∧ (¬Q ∨ R) /Distributive Law
At this point, we can run an inference algorithm on the conjunctive normal form. Occasionally, through the process of inference by resolution, we might end up in cases where a clause contains the same literal twice. In these cases, a process called **factoring** is used, where the duplicate literal is removed. For example, (P ∨ Q ∨ S) ∧ (¬P ∨ R ∨ S) allow us to infer by resolution that (Q ∨ S ∨ R ∨ S). The duplicate S can be removed to give us (Q ∨ R ∨ S).
- Empty Clause:  P and ~P = () which is an empty clause
#### Inference by Resolution
- the following is the proof by contradiction
	-   To determine if KB ⊨ α:
	    -   Check: is (KB ∧ ¬α) a contradiction?
	        -   If so, then KB ⊨ α.
	        -   Otherwise, no entailment.

-   To determine if KB ⊨ α:
    -   Convert (KB ∧ ¬α) to Conjunctive Normal Form.
    -   Keep checking to see if we can use resolution to produce a new clause.
	    -   If we ever produce the empty clause (equivalent to False), congratulations! We have arrived at a contradiction, thus proving that KB ⊨ α.
	    -   However, if contradiction is not achieved and no more clauses can be inferred, there is no entailment.
- Here is an example that illustrates how this algorithm might work:
	-   Does (A ∨ B) ∧ (¬B ∨ C) ∧ (¬C) entail A?
	-   First, to prove by contradiction, we assume that A is false. Thus, we arrive at (A ∨ B) ∧ (¬B ∨ C) ∧ (¬C) ∧ (¬A).
	-   Now, we can start generating new information. Since we know that C is false (¬C), the only way (¬B ∨ C) can be true is if B is false, too. Thus, we can add (¬B) to our KB.
	-   Next, since we know (¬B), the only way (A ∨ B) can be true is if A is true. Thus, we can add (A) to our KB.
	-   Now our KB has two complementary literals, (A) and (¬A). We resolve them, arriving at the empty set, (). The empty set is false by definition, so we have arrived at a contradiction.

#### First Order Logic
- Constant symbols
	-  Minerva
	- Pomona
	- Horace
	- Gilderoy
	- Gryffindor
	- Hufflepuff
	- Ravenclaw
	- Slytherin
- Predicate Symbol
	- Person
	- House
	- Belongs to
- How does the two combine
	- Person(Minerva)
		- Minerva is a person
	- House(Gryffindor)
		- Gryffindor is a house
	- BelongsTo(Minerva, Gryffindor)
		- Minerva belongs to gryffindor
- ###### Universal Quantification
	- ∀x. BelongsTo(x, Gryffindor) → ¬BelongsTo(x, Hufflepuff) 
- ###### Existential Quantification
	- ∃x. House(x) ∧ BelongsTo(Minerva, x) 