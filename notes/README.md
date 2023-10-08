# Section 1. Regular languages
A regular language is a category of formal languages that can be represented by a regular expression and recognized by a finite automaton.

## 1.1. Regular Expressions
Are sequences of characters that define a search pattern.

## 1.2. Deterministic finite automata (DFA) and nondeterministic finite automata (NFA)

### 1.2.1. Deterministic Finite Automata (DFA): 
This is a finite state machine where for each input symbol and current state, there is one and only one transition to a next state. This means that given a particular input and current state, the DFA can determine the next state without any ambiguity.

### 1.2.2. Nondeterministic Finite Automata (NFA): 
Unlike DFA, an NFA can have zero, one, or more than one transition from a given state for a given input symbol. This introduces the concept of nondeterminism, where multiple paths or choices are available for computation.

## 1.3. Closure properties, periodicity, and algorithmic properties
### 1.3.1. Closure Properties: 
These are properties that indicate whether the result of an operation (like union, intersection, complementation, etc.) on one or more languages (that belong to a specific class) will still belong to that same class. For instance, regular languages are closed under union, intersection, and complementation, which means that if you take two regular languages and combine them using these operations, the result will also be a regular language.

### 1.3.2. Periodicity: 
Periodicity refers to the recurrence of a pattern at regular intervals. In formal language theory and automata, this concept isn't frequently discussed under this term, but periodic behaviors can be observed in certain automata or strings. For instance, a string that repeats its pattern every nn characters can be considered to have a period of nn.

### 1.3.3. Algorithmic Properties: 
These properties are related to the algorithms and computational processes associated with a language or automaton. For instance, determining membership of a string in a regular language can be decided using a deterministic finite automaton (DFA). Decidability (whether there exists an algorithm that can always give a correct yes/no answer for every input) is a fundamental concept here. Algorithmic properties might concern questions like: Is a given language empty? Does a language accept all strings over its alphabet? Is one language a subset of another?

# Section 2. Context-free languages (CFL)
Context-free languages are a category of formal languages that are a step up in expressive power from regular languages. They can express languages that regular languages can't, but there are also languages beyond their expressive capacity. A language is context-free if there is a context-free grammar (CFG) that generates it. A context-free grammar consists of a set of production rules that are applied to generate strings in the language.


## 2.1. Context-Free Grammars
A context-free grammar is defined by four components:

   * Non-terminal Symbols (Variables): These are the symbols from which strings are derived. They are placeholders for patterns that can be replaced by other non-terminals or terminals.

   * Terminal Symbols: These are the basic symbols of the language that are not replaced during the derivation process. In the context of programming languages, these could be keywords, operators, and other syntactic elements.

   * Production Rules: These are rules that define how non-terminal symbols can be replaced by combinations of non-terminal and terminal symbols.

   * Start Symbol: One of the non-terminal symbols is designated as the start symbol. Derivations begin from this symbol.

A context-free grammar GG can be represented as:
G=(N,T,P,S)G=(N,T,P,S)
Where:
    * NN is a finite set of non-terminal symbols.
    * TT is a finite set of terminal symbols.
    * PP is a finite set of production rules.
    * SS is the start symbol and S∈NS∈N.
Example:
Consider a simple CFG for balanced parentheses:
    N={S}N={S}
    T={(,)}T={(,)}
    PP consists of the following rules:
        S→SSS→SS
        S→(S)S→(S)
        S→ϵS→ϵ (where ϵϵ represents the empty string)
    SS is the start symbol.

This grammar can generate strings like "()", "(())", "()()", and so forth.

CFGs are central to the design of compilers for programming languages. The syntax of a programming language is often described using a context-free grammar, which provides a structured way to parse and understand the source code of programs written in that language.

## 2.2. Pushdown Automata 
A pushdown automaton is a computational model used in the theory of computation to recognize context-free languages. It's essentially a finite automaton with an added feature: a stack that can be used as a memory mechanism.

### 2.2.1.  Components of a PDA:
  * A set of states.
  * A set of input symbols (input alphabet).
  * A set of stack symbols (stack alphabet).
  * The stack, which can hold an infinite sequence of stack symbols.
  * A transition function, which describes how the PDA moves between states, consumes input symbols, and manipulates the stack.
  * A start state.
  * A start stack symbol (initial symbol to begin with on the stack).
  * A set of accepting states.

#### 2.2.2. Working:
  * A PDA reads the input symbols one by one.
  * Based on the current state, the current input symbol, and the top symbol on the stack, the PDA decides the next state to move to, whether to advance to the next input symbol or not, and how to manipulate the stack (either push a new symbol onto it or pop the top symbol off).

### 2.2.3. Recognition Modes:
  * Accept by Final State: The PDA accepts an input if, after reading the entire input, it reaches one of the accepting states.
  * Accept by Empty Stack: The PDA accepts an input if, after reading the entire input, its stack is empty.

### 2.2.4. Expressiveness:
  * PDAs are equivalent in power to context-free grammars. This means that for every PDA, there's a context-free grammar that generates the same language and vice versa.
  * PDAs can recognize many languages that regular finite automata cannot. For instance, the set of balanced parentheses is recognizable by a PDA but not by a regular finite automaton.

### 2.2.5. Deterministic vs. Non-deterministic PDAs:
  * Deterministic Pushdown Automata (DPDA) always know the next state, given their current state, input symbol, and top stack symbol.
  * Non-deterministic Pushdown Automata (NPDA) can have multiple possible next states for the same combination of current state, input symbol, and stack symbol. NPDAs are more expressive than DPDAs in terms of the context-free languages they can recognize.

Pushdown automata are foundational in the study of formal languages and automata theory and have practical applications, particularly in the parsing phase of compiler design.

## 2.3. closure properties and periodicity
### 2.3.1. Closure Properties for CFLs:
  * **Union**: If L1L1​ and L2L2​ are two context-free languages, then their union L1∪L2L1​∪L2​ is also context-free.
  * **Concatenation**: If L1L1​ and L2L2​ are two context-free languages, then their concatenation L1L2L1​L2​ is also context-free.
  * **Star**: If LL is a context-free language, then its Kleene star L∗L∗ is also context-free.

However, CFLs are not closed under some operations:
  * **Intersection**: The intersection of two context-free languages might not be context-free.
  * **Complement**: CFLs are not closed under complementation. If LL is a context-free language, its complement (over the alphabet of LL) might not be context-free.
  * **Difference**: The difference between two context-free languages might not be context-free
### 2.3.2. Periodicity:
While the concept of periodicity is often discussed in relation to regular languages and strings, its exploration within the realm of context-free languages is less common. Nevertheless, periodic behaviors can be observed in certain context-free languages.

For a context-free language, it's not as straightforward to talk about periodicity as it is with regular languages, because context-free languages can generate strings with nested structures (like balanced parentheses), which don't exhibit simple repetitive patterns. However, certain subsets of a context-free language or certain derivations might exhibit periodic behaviors, but this would need to be analyzed on a case-by-case basis.

# Section 3. Turing Machine

## 3.0. Components:
  * **Tape**: An infinite length of tape divided into cells. Each cell can contain a symbol from a given alphabet, or it can be blank.
  * **Tape Head**: This reads and writes symbols on the tape and can move left or right.
  * **State Register**: It stores the current state of the Turing machine. The machine starts in the initial state and can transition to other states or halt.
  * **Transition Function**: Describes how the machine behaves. It specifies, given the current state and the symbol under the tape head, what symbol to write, how to move the tape head (left or right), and what the next state should be.

## 3.0.1. Operation: At any step, based on the current state and the symbol under the tape head, the machine will:
  * Write a symbol to the current cell (which could be the same symbol or a different one).
  * Move the tape head one cell to the left or right.
  * Transition to a new state or remain in the current state.

    **Halting**: The machine will stop its operation if it enters a designated "halt" state.

## 3.0.2. Deterministic vs. Non-deterministic: 
A deterministic Turing machine (DTM) has exactly one action specified for any given state/symbol combination. A non-deterministic Turing machine (NDTM) can have multiple possible actions for a given state/symbol combination.

## 3.0.3. Applications: 
While Turing machines are primarily a theoretical construct, they have had profound implications for the study of algorithms, decidability, complexity theory, and the very nature of computation. They form the basis for understanding the limits of what computers can and cannot do.

## 3.1. Computability
When talking about Turing machines, computability refers to the study of what can and cannot be computed by these machines. The concept of a Turing machine has become central to the understanding of the boundaries of algorithmic computation.

### 3.1.2. Computable Functions:
A function (from natural numbers to natural numbers, for simplicity) is said to be computable if there exists a Turing machine that, given an input representing nn, halts with an output representing f(n)f(n) for that function ff.
Any function that can be described by an algorithm can be computed by some Turing machine.

### 3.1.3. The Church-Turing Thesis:
This is an informal hypothesis that suggests that any function computable by a "reasonable" mechanical computation model can be computed by a Turing machine. This isn't a theorem to be proved, but an axiom that underlies the study of computability.
In essence, it posits that Turing machines capture the intuitive idea of "computation."


## 3.2. Types of Turing Machines

### 3.2.1. Deterministic Turing Machine (DTM):
In a DTM, for every state and symbol combination, there's exactly one action specified (write a symbol, move the head, transition to another state).
A deterministic Turing machine is the most basic form of Turing machine and often the one first introduced in computational theory.

### 3.2.2. Non-deterministic Turing Machine (NDTM):
An NDTM has the ability to be in multiple states simultaneously. For a given state and symbol combination, multiple actions might be possible.
NDTMs are more powerful in terms of speed (they can solve problems faster) but are not more powerful in terms of what they can compute when compared to DTMs.

### 3.2.3. Universal Turing Machine (UTM):
A UTM can simulate any other Turing machine. It takes, as its input, an encoding of a Turing machine and an input for that machine and then simulates that machine's behavior on the given input.
UTMs are central to the concept of universal computation, suggesting that certain machines (or computers) can, in principle, compute anything computable.

### 3.2.4. Multi-tape Turing Machine:
This variant has multiple tapes, each with its own tape head. The machine can read or write to several tapes at once.
While they seem more powerful, multi-tape Turing machines are computationally equivalent to standard Turing machines. However, they can make some computations more efficient.

### 3.2.5. Enumerators:
An enumerator doesn't have an input tape but outputs strings onto its tape. It is used to generate (or enumerate) strings from a language, potentially in a non-decreasing order.

### 3.2.6. Quantum Turing Machine:
A theoretical model of quantum computation. Quantum Turing machines use the principles of quantum mechanics to potentially solve certain problems more efficiently than classical Turing machines.
They can be in a superposition of many states at once, which allows them to explore multiple solutions simultaneously.

### 3.2.7. Probabilistic Turing Machine:
This machine can make moves based on probabilities. It's a theoretical model used to study the power of randomness in computation.

### 3.2.8. Counter Machines:
A simplified form of the Turing machine where computation is done using one or more counters, and the actions involve incrementing, decrementing, or testing these counters.

### 3.2.9. Read-only Turing Machine:
The machine can read from the input tape but can't write to it. It usually has a separate tape for computation.

### 3.2.10. Linear Bounded Automaton (LBA):
A restricted form of the Turing machine where the tape is limited to a length linearly proportional to the input length. LBAs are used to recognize context-sensitive languages.

For practical purposes, despite their differences, all these Turing machines (excluding the LBA) are equivalent in terms of what functions they can compute, affirming the Church-Turing thesis that they all capture the notion of algorithmic computation.

## 3.3. Decidability
### 3.3.1. Decidable Problems:
A problem (or language) is decidable if there exists a Turing machine that accepts all inputs in the problem and rejects all inputs not in the problem, and importantly, it halts on all inputs.
The machine will always provide an answer and will never loop indefinitely.
An example of a decidable problem: "Is this given integer even?"

### 3.3.2. Undecidable Problems:
A problem is undecidable if no Turing machine can solve it for all possible inputs. This means that for any proposed machine, there will be some inputs for which the machine will loop forever.
The most famous undecidable problem is the Halting Problem. It asks, given a description of a Turing machine and an input, whether the machine will eventually halt on that input. Alan Turing proved that this problem is undecidable because no general algorithm can predict whether a given Turing machine will halt or run forever for all possible inputs.

### 3.3.3. Semi-decidable (or Turing Recognizable):
A problem is semi-decidable if there exists a Turing machine that halts and accepts for strings in the language but might run forever for strings not in the language.
This means that while we can confirm a positive answer (by halting and accepting), we might never get a confirmation of a negative answer (the machine might run indefinitely).
Every decidable language is also semi-decidable, but the reverse isn't true.
An example: The problem of determining if a given Turing machine accepts a particular string is semi-decidable. If it does, we'll eventually know. If it doesn't, the machine might run forever.

### 3.3.4. Reductions and Proving Undecidability:
Often, undecidability of a problem is established through a reduction from another problem that's already known to be undecidable.
A classic technique is to reduce the Halting Problem to another problem. If we could solve this new problem algorithmically, we'd be able to solve the Halting Problem, leading to a contradiction.

### 3.3.5. Implications:
Discovering undecidability is profound. It tells us that there are limits to what can be known or solved algorithmically, no matter how powerful our computers are.
It's essential to distinguish between "unsolvable" in practical, everyday terms (like a very hard puzzle we can't figure out) and "undecidable" in the theoretical, Turing-machine sense, where no algorithm exists at all to solve the problem for all possible input

    
