# Asynchronous Gossip and Push-Sum Algorithms in Pony

This project simulates two algorithms, Gossip and Push-Sum, for distributed information propagation and sum computation using asynchronous actors in Pony. The system can be run on different network topologies, and the time to convergence is measured for each scenario.

## Team Members
- **Shruthi Yaramada**
  UFID: 2649 7222
- **Yaswanth Attaluri**
  UFID: 1013 6560

## Project Overview
This project simulates two distributed algorithms one is Gossip and the other is Push-Sum using the actor model in the Pony programming language. The goal of this simulation is to measure the convergence time of both algorithms across different network topologies using a number of actors as nodes.

## Topologies
The network of actors can be set up in the following topologies:
1. **Full Network**: Each actor is connected to every other actor.
2. **3D Grid**: Actors form a 3D grid, where each actor has six neighbors.
3. **Line**: Actors are arranged in a line, and each actor has up to two neighbors.
4. **Imperfect 3D Grid**: Similar to the 3D grid but with one additional random neighbor for each actor.

## Algorithms
### Gossip Algorithm
### Description: Gossip algorithms are used for information propagation in distributed networks. Each actor (node) starts by receiving a rumor and continues passing it to a randomly chosen neighbor. The actor stops propagating the rumor after hearing it 10 times.
### Steps:
1. One actor starts the rumor.
2. Every actor chooses a random neighbor and sends the rumor.
3. Each actor keeps a count of how many times it has received the rumor.
4. An actor terminates after hearing the rumor 10 times.

### Push-Sum Algorithm
- Each actor maintains two values, s and w, where s = i (the actor’s ID) and w = 1.
- Actors exchange half of their s and w values with random neighbors.
- An actor terminates if the ratio s/w does not change significantly (within 1e-10) over three consecutive rounds.

## Input Format
The program is run using the following command:



I want the same above information in this format

