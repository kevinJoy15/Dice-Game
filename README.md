# Dice-Game
Using Full-Value Iteration to solve the Dice Game


from yt video: https://www.youtube.com/watch?v=d5gaWTo6kDM

basic understanding:

R(s) in this 'R' is the reward function and 's' is the state.
The state 's' tells the position of the particular object.

For an example of a chess game:

- if u win R(s) = +1
- if u lose R(s) = -1
- if u tie R(s) = 0

Credit assignment problem:
So in a game of chess if the R(s) is -1 which means it lost but the algorithm doesn't know on which step it made a mistake suppose on move 20 it made a mistake that cost him the entire game and from there the next 30 moves were of no use. This problem of understanding the process chain is the credit assignment problem.

MDP (Markov Decision Process)

- used to solve reinforcement learning
- it is a 5 tuple that consists of {S,A,{P<sub>SA</sub>},&,R}
- S - set of states (different positions, orientations, etc.)
- A - set of actions (movements, or actions)
- PSA - State transition probability (if u do a particular action A from a particular state S what is the probability of u reaching another state S' S prime)
- & - Discount factor (value between 0 and 1)
- R - reward function

Eg:

![87f097e8d3216609a4863fbe74e8c46a.png](file:///C:/Users/kevin/.config/joplin-desktop/resources/19909e411f1540989ef5d0afbf00ff23.png)

The main aim of the robot is to move to the +1 square. And the black box represents a wall or object it cant pass.

When moving the robot has a 0.8% chance it moves in the right direction and a 0.1 to move either left or right, this might be caused due to wheel slip.

![0a2e2b2736d40b674b7cb3d34fcf7d77.png](file:///C:/Users/kevin/.config/joplin-desktop/resources/8e53b30c3da34141b7c8c86388ec94d1.png)

adding index values as references, we get:
![a7ec6a4e0e9fb01225f7d4aa38bc7cb5.png](file:///C:/Users/kevin/.config/joplin-desktop/resources/faba73e89e82457aad528f4792414a9e.png)

The actions that can be taken by the robot are moving from either {N,S,E,W}.

assuming the robot is in the position (3,1)
the probability for most of its actions to go to the +1 part is

P<sub>(3,1)N</sub>(3,2) = 0.8
this means from the position 3,1 the chance of the robot moving to (3,2) is 0.8 percent.

P<sub>(3,1)N</sub>(4,1) = 0.1
P<sub>(3,1)N</sub>(2,1) = 0.1
because of wheel slips

P<sub>(3,1)N</sub>(3,3) = 0
this is due to the fact that the robot cant skip a block

We know that the P(s) of the winning block is +1 and the losing block of P(s) = -1
hence all the other blocks P(s) are set to a low value of -0.02. Hence the main goal of the robot is to get to the +1 space by by reducing the total number of penalties.

Hence the order of actions would go as follows

at S<sub>0</sub>
choose action A<sub>0</sub>
it moves to new state which is distributed to the action of the previous action S<sub>1</sub>NP(S<sub>0</sub> A<sub>0</sub> )

chooses new action A<sub>1</sub>
S<sub>2</sub>NP(S<sub>1</sub> A<sub>1</sub> )
.
.
.

this continues until it reached +1

Total payoff: R(S<sub>0</sub>) +&(S<sub>1</sub>) +&<sup>2</sup>R(S<sub>2</sub>)+...

we assume gamma (&) to be a number just below 1, 0.99. This is used to increase time complexity and decrease time waste.

hence the goal of reinforcement learning is to decrease the total payoff time.

Policy (π): maps from S -> A
optimal policy is essentially the best way for an algorithm to work.

![b8607b26ecb0095471b54115e107b812.png](file:///C:/Users/kevin/.config/joplin-desktop/resources/148d528023b2497db07d3e673a1073e9.png)

this is the policy for the robot to move.

but if the robot is at 3,1 it makes more sense for it to move upward to provide the ideal solution but that is a tradeoff in mdp where the longer path is the best path.

* * *

from yt video: https://www.youtube.com/watch?v=d5gaWTo6kDM
