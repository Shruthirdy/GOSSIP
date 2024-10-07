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
1. **Full Network**: Every actor can communicate with all other actors.
2. **3D Grid**: Actors are arranged in a 3D grid, and each actor can only communicate with its adjacent neighbors in the grid.
3. **Line**: Actors are arranged in a straight line, with each actor having two neighbors (one on the left and one on the right, except for the endpoints).
4. **Imperfect 3D Grid**: Similar to the 3D grid, but each actor also has one random neighbor outside the grid.

## Algorithms
### 1. Gossip Algorithm
#### Description 
Gossip algorithms are used for information propagation in distributed networks. Each actor (node) starts by receiving a rumor and continues passing it to a randomly chosen neighbor. The actor stops propagating the rumor after hearing it 10 times.
#### Steps:
1. One actor starts the rumor.
2. Every actor chooses a random neighbor and sends the rumor.
3. Each actor keeps a count of how many times it has received the rumor.
4. An actor terminates after hearing the rumor 10 times.

### 2. Push-Sum Algorithm
#### Description 
Push-Sum is an algorithm for distributed sum computation. Each actor maintains two quantities sum_value (s) and weight_value (w). The ratio s/w approximates the total sum distributed among actors. An actor keeps sending its halved sum and weight to a randomly selected neighbor until the ratio s/w converges (i.e., doesn't change significantly for 3 consecutive rounds).
#### Steps
1. Each actor maintains initial values s = i (actor ID) and w = 1.
2. After receiving a message (s, w), an actor adds the received values to its own s and w.
3. It then halves its sum and weight, sends one half to a random neighbor, and keeps the other half.
4. The actor terminates if its ratio s/w changes less than 10^-10 for 3 consecutive rounds.

## Project Implementation
#### 1. Main Program:
The program accepts the following command-line arguments: <numNodes> <topology> <algorithm>.
-> total_nodes: Total number of actors (nodes).
-> topology: The network topology (full, 3D, line, imp3D).
-> algorithm: The algorithm to run (gossip, pushsum).

#### 2. Topologies:
-> Functions build_full_topology, build_3d_topology, build_line_topology, and build_imperfect_3d_topology are written to build the respective network topologies.
-> Each node is assigned its neighbors based on the chosen topology.

#### 3. Gossip Algorithm:
Actors pass the rumor to randomly selected neighbors. The algorithm terminates once each actor has received the rumor 10 times.

#### 4. Push-Sum Algorithm:
Each actor maintains its sum_value(s) and weight_value(w) and communicates updates with random neighbors. The algorithm terminates when the ratio s/w reaches a stable value.

#### 5. Termination:
The Boss actor controls the system and terminates the simulation once convergence is achieved for the chosen algorithm.

## Running the Project
The project can be compiled and run with the following command:

```bash
./GOSSIP <total_nodes> <topology> <algorithm>
```
Example
```bash
./GOSSIP 10000 imp3D gossip
```

## What Is Working
1. Both Gossip and Push-Sum algorithms are implemented.
2. The project supports all the required topologies (full, 3D, line, imperfect 3D).
3. Convergence time is correctly measured and displayed for different network sizes and topologies.

## Largest Network Handled:
Full Network: 10,000 nodes.
3D Grid: 10,000 nodes.
Line: 10,000 nodes.
Imperfect 3D Grid: 10,000 nodes.


