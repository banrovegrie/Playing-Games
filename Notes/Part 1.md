# Part I

# Computation and information

---

# Modelling Computation

---

Computation has a lot of models, that is there are many ways to describe computation. In general you can say that computation occurs in a well defined manner, we use `Algorithms` to describe a computation.

## Algorithm

An algorithm is the set of rules to be followed to perform a computation, these steps take us from the initial state to the desired state. The set of rules is finite and well defined without any ambiguity.

Any computation can be well described in terms of an algorithm. For example, let's define an algorithm to check if a given string is a palindrome:

1. Measure the length of the input, name it `n`.
2. Set 2 pointers `start` and `end` at the 1st and the last character respectively.
3. Check the characters under the 2 pointers, if same then go to step 4, else go to step 6
4. Increment the `start` pointer position and decrement the `end` pointer position.
5. If the distance between the 2 pointers is less than 2, Go to step 7.
6. Since the characters did not match, the given string is not a palindrome. Stop computing.
7. Since we have successfully matched all the characters, the given string is a palindrome.

### The issue with such modelling

For a person who understands the language that the algorithm is written in, they will have no issues following it as long as they are aware of the terms used in it.

The algorithm mentioned above has an ambiguity that is overlooked by us due to certain valid assumptions. But there is a need for a better and more concrete definition of what an algorithm is for a required computation. 

And since the invention of computers, the need for such a description has only increased since the computers can not understand such high-level rules. This issue was resolved by Alan Turing with the help of **Turing machines.**

# Turing Machines and Universality

---

A mathematical model of description with definite rules and definitions. Turing machines were developed in 1935 to accurately describe what computation is, It was developed independently independent of lambda-calculus which is equivalent to Turing machines.

These abstract machines even though simplistic, have the capacity to run any computation algorithm described to it, making it equivalent to any other form of computer. This is the **Church-Turing Thesis.**

## Physical description

---

A Turing machine can be described physically with 3 parts, those are:

- Finite state automaton
- Infinite tape(s) with discrete cells
- head(s) for each tape.

## Formal description

---

Formally, A Turing Machine is described as a 7 tuple $\lang Q, \Gamma, \Box, \Sigma,  \delta, q_{start}, 
q_{halt}\rang$

$Q$ is the set of all states in the finite state automaton embedded in the Turing Machine.

$\Gamma$ is the set of symbols which are allowed on the tape.

$\Box$ is the blank symbol which occurs on the tape when it has not been accessed. $\Box \in \Gamma$

$\Sigma$ is the set of symbols which can be written on the tape by the head. $\Sigma \subset \Gamma$

$\delta$ is the transition function which decides how the machine works.

$\delta : (Q \backslash \{q_{acc}, q_{rej}\}) \times \Gamma \rightarrow 
(Q \times \Gamma \times \{L, R\})$

$q_{start}$ is the start state of the machine.

$q_{halt}$ is the halt state, when a Turing Machine reaches this state it halts with the output on the tape.

## Working of a Turing Machine

---
A Turing machine $M = (Q, \Sigma, \Gamma, \delta, q_{0}, q_{accept}, q_{reject})$ computes as follows. Initially, M receives its input $w = w_1w_2...w_n \in \Sigma^∗$ on the leftmost n squares of the tape, and the rest of the tape is blank. The head starts on the leftmost square of the tape. The computation proceeds according to the rules described by the transition function. 

The **transition function** as described earlier are functions that take the current state and the symbol below the tape's head as the input. The output is the symbol written back onto the tape, the new state of the machine, and the direction of movement of the head.

The computation continues until it enters either the accept or reject states, at which point it halts. If neither occurs, M goes on forever.

As a Turing machine computes, changes occur in the current state, the current tape contents, and the current head location. A setting of these three items is called a **configuration** of the Turing machine. The configuration can be represented as $uqv$, where $q$ if the current state, the current tape contents is $uv$ and the head locatoin is the first symbol of $v$.We say that configuration $C_1$ yields configuration $C_2$ if the Turing machine can legally go from $C_1$ to $C_2$ in a single step.

The **start configuration** of $M$ on input $w$ is the configuration $q_0w$, which
indicates that the machine is in the start state q0 with its head at the leftmost
position on the tape. In an **accepting configuration**, the state of the configuration is $q_{accept}$. In a **rejecting configuration**, the state of the configuration is $q_{reject}$.

A Turing machine M accepts input w if a sequence of
configurations $C_1, C_2,..., C_k$ exists, where
1. $C_1$ is the start configuration of M on input w,
2. each $C_i$ yields $C_{i+1}$ , and
3. $C_k$ is an accepting configuration.

The collection of strings that M accepts is the language of M, denoted as L(M). We call a language Turing-recognizable if some Turing machine recognizes it.

## Robustness of the Turing Machines

The equivalency of Turing Machines with respect to the power i.e the ability to solve problems stays same for a lot of variance in the design. This property is referred to as **robustness**. The turing machine is remarkably robust. There are many variation on the definition of a Turing machine. Eg, Change in Tape alphabet, Multitape TM, Multiple heads TM, Non-deterministic TM, etc. But they all have equivalent power, i,e. they recognize same class of languages. To show that two kinds of machines are equivalent, we show how to simulate the behavior of one using the other.

## Universal Turing Machines

---

universal Turing machine (UTM) is a Turing machine that simulates an arbitrary Turing machine on arbitrary input. The universal machine essentially achieves this by reading both the description of the machine to be simulated as well as the input to that machine from its own tape.


# Church Turing Thesis

---

The Church-Turing thesis tells us that all effective models of computation are no more
powerful than a Turing machine. The Church-Tur­ing the­sis has not and can not be proven. The only way to know that every compu­ta­tion can be expressed in some lan­guage is to know what every compu­ta­tion is. But it is almost uni­ver­sally believed. We’ve found myr­iad ways of describ­ing compu­ta­tions and all of them have been reducible to Tur­ing machi­nes. We have no evi­dence that any more pow­erful means of describ­ing processes exists.