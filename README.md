# DFA-Minimization-Java
--------------------------------------------------------------------------------------------------------------------
Summary
This program that takes a deterministic finite state machine and produces an equivalent one with a minimal number of states.

For more information on deterministics FSMs, see https://en.wikipedia.org/wiki/Deterministic_finite_automaton

Algorithm Description (content taken from slides by Emil Sekerinski)
Given a deterministic finite state machine A = (T, Q, R, q0, F), this program constructs an equivalent reduced deterministic finite state machine A' = (T, Q', R', q'0, F') as follows:

Remove all unreachable states from Q (using DFS).
Construct the states Q' as a partition of states of Q by successive refinement. Initially let there be two groups, F and Q - F. Sets are represents are bitsets in C for efficiency.
For each group G in Q', partition G into subgroups such that two states q, r of G are in the same subgroup if and only if for all t in T, states q and r have transitions on t to states in the same group of Q', or both don't have transitions on t.
Replace group G with its subgroups and repeat last step until no group is further refined.
Constraints
This program can only convert FSMs which have a vocabulary size of less than or equal to 26, and the vocabulary symbols must be translated to the letters a-z. Also, this program can only convert FSMs which have a state size of less or equal to 63, and these state numbers must be transated to 0-63.

Input/Output
The program reads description of a deterministic finite state machine from standard input and produce an equivalent deterministic finite state machine on standard output. The states in the input are represented by integers 0, 1,..., 63 and the symbols by characters a, b, ..., z.

The first line of the input is the initial state.
The second line contains the final states, separated by blanks.
Each subsequent line is a transition asa triple with a source state, a symbol, and a target state, separated by blanks.
The output is analogous. Remember that the state numbers of the reduced FSM have no relevance to the state numbers of the original FSM.

Sample input:
0
2 5
0 a 1
1 b 2
0 b 3
3 a 4
4 b 5

Sample output:
3
0
1 b 0
2 a 1
3 a 1
3 b 2

Make and run
This program can be compiled using gcc and does not require any third party libraries.
