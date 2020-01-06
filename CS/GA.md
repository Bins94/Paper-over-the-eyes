# Genetic algorithm

## An intruduction to Genetic algorithms
https://www.boente.eti.br/fuzzy/ebook-fuzzy-mitchell.pdf
Predicting dynamical systems
independent variables
2 GA in problem solving
Evolving lisp programs:
  Tree-base:
  Parse tree from lisp expression: operation as node, arguments as leaves.
  crossover: select a random point of parents and exchange their subtree.
  mutation: generate and replace the subtree.
  Stack-base:
  evolved program which can explicitly generate a lisp programs include iteration and jugement.
Evolving cellular automata
  one-dimensional binary-string callular automaton.
  Rule to evolve: state of a bit is influence by the nearest neighbor.
  The goal: after some steps, the binary-string calculate the density of 1/0 in the string, and the string become all 1/0 string.
  The rules evolved by GA perform some special pattern and probably corresponding operation in space-time diagram. And process the IC with these operation correspondly perform a similar result. This is emergent computation: a patial simple rule can perform a complex behavior in global.  
Date analysis and prediction:
  Prediction of stock market: predict the price of a specified stock by its historical price.
  Mackey-Glass equation.
Predicting protein structure
  46 amino acid and 10 torsion angles.
  fitness function: low potential energy.
Evolving neural networks
  1. evolving weights in a fixed network
  GA has a greater performance than the back-propagation.
  back-propagation: find a local maximum by patial derivative.
  2. evolving network architectures
    dircted encoding
    grammatical encoding
    evolving a learning rule: no hidden layers.
3 Scientific model
  A simple model of baldwin effect
  A individual is a neural-network with 25% '1/0' and 50% '?' IC.
  "zone of increased fitness" to smooth the fitness lanscape.
  Fitness: refer to the number of trials needed 1+19*n/1000(1000 learning trials)
  Selection: single-point crossover, probability proportional to its fitness. No affected by the learning.
  Evolutionary reinforcement learning
  evaluation netwrok( fixed from birth):
    input: state of agent at time t
    output: a judgment about how good that the state is for the agent.
  action network( change over agent's ancestors, according to reinforcement learning algorithm):
    input: state of agent at time t
    output: what action is taken( move from the current lattice site to one of the four neighboring sites)
  The action can result in eating, be eaten, and less radical consequence. The agent keep the energy above a certain level to prevent death and reproduce once it has enough enerage in it( low probability of mutation). Two spactially nearby agent can produce offspring(crossover). No fitness function.
  calculate how long a population can survive:
    ERL(evolution plus learning)
    E(evolution alone with no learning)
    L(learning without evolution)
    F(fixed random weights)
    B(ignore any input and crossover)
  Mathematical model for sexual selection
    P(preference) gene: female preference for a particular trait T( female only).
    T(trait) gene: trait T( male only), male with it less likely to survive.
    Initial population with equal number of female/male, t/p.
    A certain number of male with t will be killed off before reproduction. Each female chose a surviving male to mate with.
    Mating with probabilistically as a function of the value of P and T.
    Experiment 1:
    Observe the P/T fraction of population while the simulation start with a different P/T fraction of population.
    Experiment 2:
    How does a male with trait invade a population?
    Start with no population of T and T can be occured by mutating.
  Modeling ecosystems
    Echo: model of ecological system
    The world( a two-dimensional lattice contained resource) is populated by "agents".
      genotype of agent: a set of rules that govern the types and quantities of the agent need( live, reproduce).
      phenotype of agent: result behavior and physical appearance.
      interaction between agent: combat, trade, mating. Chose one of these interaction base on agent's internal rule and outward physical appearance of other agent.
        combat: The loser will die and its resources are added to the winner after combat.
	trade: Less warlike will chose trade. Trade any resources they need to reproduce. Deception can be evolved.
	mating: base on agent's internal rule and appearance of potential mate. After reproducing, the parents die and the offspring replace their site.
    experiment: rank-abundance plot, calculate the abundance of genotypes.

    Strategic bugs
    The world is a two-dimensional lattice contained only bugs and food.
      sensory data: from five sites centered on the bug's current site. (00=least food, 01=more food, ...)
      vector( movement): directions and distance.
      lookup table: correctsponding vector base on the sensory data.( gene encode)
      baseline usage( u0): random selection of gene.
      activity wave: u-u0.

  Optimizers vs. Satisficers( maximizers)
  Implications for GA performance
    Hybird methods could be better than GA alone.
    Hill climber.
    Gradient search.
  Deceiving a GA
    Misleading information about where to optmize.
  Limitations of static schema analysis.
    Given any low-order, short-defining-length hyperplane partition, a GA is expected to converge to the hyperplane with best static average fitness.
    Deceptive fitness will be difficult for a GA.
    Reason:
      Collateral convergence
      High fitness variance
4 Royal roads
  Royal roads function: a class of fitness landscapes that were meant to capture the essence of building blocks in idealized form.
  Building block features of fitness landscapes:
    low-order, higher-fitness schemas
    intermediate-order, higher-fitness schemas
  Experimental results
  The number of offspring of individual i:
    1 + (Fi - mean(F))/sigma(F)
    mean(F) is the mean of F
    sigma(F) is standard deviation
    cut off at 1.5
  Sheepest-ascent hill climbing( SAHC)
    1. Start at random current-hilltop.
    2. Systematically flip each bit from left to right. Recording it's fitness.
    3. If fitness increase, set it to current-hilltop.
    4. If no fitness increase, save current-hilltop and go to step 1/2.
    5. Return the highest fitness.
  Next-ascent hill climbing( NAHC)
    1. Start at a random current-hilltop.
    2. Flip bit from 0 to l. If fitness increase, repeat step2 with new current-hilltop.
    3. If no increases, save current-hilltop that was found.
    4. Return highest hilltop.
  Random-mutation hill climbing( RMHC)
    1. Start at a random current-hilltop.
    2. Choose a random locus to flip. If it has an equal or higher fitness, set as best-evaluated string.
    3. Go to step 2 until get the desirable result.
    4. Return.
  Analysis of RMHC
  !(Use schemas to analyse the mutation lost)
  Hitchhiking in the GA
    When the S1 is not independent. The zero in S1 will spread in the population while S2 is higher-fitness schema. The S1 will be drowned. !S1 was "hitchhiking". 
  An idealized GA
  IGA( need to know what schemas explicitly desired):
    1. choose a new string at random
    2. Sequester the string contain desired schemas.
    3. When a string contain no-yet-discovered schemas, crossover with Sequestered string.
    'Pn(t): Probability of n schema is desired can be discovered after t timestep.
    p: probability of find out H on random string.
    q: !p, not found
    'Pn(t) = (1-(q^t))^n
    Pn(t): Probability of the last schema will be found at timestep t while it is not found at timestep t-1
    Pn(t) = Pn(t) - Pn(t-1)
          = (1-(q^t))^n - (1-(q^(t-1)))^n
    To get the expected time
    En(t) = sum[0,t](t*Pn(t))
          = sum[0,t]((1-(q^t))^n - (1-(q^(t-1)))^n)
  Formalization of GAs
    1. Calculate the fitness of each string.
    2. Choose two parent from population base on its fitness.
    3. Crossover the two parent. Select one of the offspring at random and discard the other( The population is always the same).
    4. Mutate each bit in the selected offspring with probabaility Pm. Put it in the population.
    5. Go to step 2 until a new population complete.
    6. Got to step 1.
    i is the interge of string
    pi(t): The proportion of population at generation t consiting of i.
    si(t): The probability of ith offspring will be selected as parents.
    ->x ~ ->y: vector differ only by a scalar factor.
    ri,j(0):
  F->s(t): fitness matrix
  G->s(t): G operator. From ->s(t) to ->s(t+1)
  M->s(t): recombination operator( crossove&mutation)
  G(->s(t)) ~ ->s(t+1)
  if G(->s(t)) = s(t), GA will not move away.
  A finite-population model( GA with Markov chain)

## Introduction of Genetic Programming
https://www.win.tue.nl/ipa/archive/falldays2007/HandoutEggermont.pdf
individuals: Each of those possible solutions.
fitness: evaluated to determine how well it solves the problem.
EP: Evolution programming
ES: Evolution strategies, for paramenter optimization
GA: Genetic Algorithms.
Step:
  initialization of population: maximum tree depth, terminal, internal node.
  genetic operators:
    crossover: from two or more parent
    mutate: from a single individual, make small changes of an individual.
    
## Tutorial of GA
http://www.cs.colostate.edu/~genitor/MiscPubs/tutorial.pdf
1. Encodings and Optimization problems( case of input parameters optimization)
  nonlinear: it's not possible to treat each paramenter as an independent.
  encoding: continuous/discretized parameters.
  offspring generating and evaluation.
  encoding: range 2^L, L-dimensional hypercube.
  evaluation: performance of optimization.
  fitness: performance -> reproductive opportunities.
  selection: select randomly by Fi/average(F) chance.
  4. The schema theorem
  M(H, t+i)/M(H, t) = f(H, t)/mean(f):
  M(H, t+i) = M(H, t)f(H, t)/mean(f)
  M(H, t+i) >= (1-p)M(H, t)f(H, t)/mean(f) + p*f(H, t)/mean(f)(M(H, t)(1 - disruption))
  H: width of string for corossover
  t: offspring
  M(): number of sample of t
  The offspring generate by fitness, keep the number increate.
  Linkage: phenoment of a set of bit act as "coadapted alleles" that tend to be inherited togather as a group.
  inversion: move linkage of bit on the chromosome.
  The probablity of randomly chosen H
  P(H,t) = H/M(H,t)
  Distuption:
  (1-P(H,t))*H/(L-1)
  (not chosen)*(how many point can be crossover)/(how long is the string)
  mutation => distruption
  premature convergence:
  fitness raise, variance reduce => need fitness scaling
  probability of crossover determin by crossover point

## 
https://www.obitko.com/tutorials/genetic-algorithms/ga-basic-description.php

#
http://web.cecs.pdx.edu/~mm/ecal92.pdf
Building-blocks hypothesis: new schemas are discovered by combineing( crossover) instances of low-order schemas( composite solution).
Fitness lanscapes feature:
1. deception:
  GA-deceptive: low-order schema misleading the GA away from fittest higher-order schemas.2. sampling error:
  High variance in the fitness of a correct low-order schema leads to sampling error that misleads the GA.
3. ruggedness:
1. Hierarchical structure of schemas, and steping stone.
The royal road function:
F(x) = sum[Search space]Cs*Sigma(x).
Cs is a value assigned to the schemas
Sigma: if x is an instance of s, if the schemas is desirable, Sigma(x)=1, otherwise 0.
The royal road function is for GA performance analysis. Cs, Sigma() are assigned by your self. That means you need to know which schemas is desired by the system, or they are self-defined values which help to build the fitness landscape.
2. Isolated High-fitness Regions.
The highest fitness is isolated from lower-order schemaswith lower fitness.
3. Multiple conflicting solutions.
Landscapes with multiple conficting solutions can be difficult for GA.
GA performance on Royal Road function
  1. All of the desired schemas are known. Search can be studied in detail by tracing the individual schemas.
  2. The effect of varied landscape can be studied.
  3. Easy to compare the performance.
  Deception
    Delect intermediate level stepping stone.
    Modify the steepness of increase in the coefficients.
Three basic questions of royal road function studying:
  The effect of crossover on GA's performance
  The effect of crossover on the waiting time for discover desirable schemas.
  Time of crossover:
    1. Time for low-order components to appear.
      Measuring time of a higher-order combination occurring while two low-order is already in population.
    2. Time for two instances to crossover in the right ways.
      Record the original discovery time. Record the discovery time when the instances(low-order) persiste in the population for at least 10 generations.
  Building blocks hypothesis: low-order of a desired schemas are present in the population. These components will combine relatively quickly. So, appearing low-order componects take longer time.
  The effect of intermediate levels on GA's performance.
    When a low-order is discovered, it will rise quickly in the population while other low-order will drop significantly.


## Formailizing genetic algorithms
https://library.eecs.utk.edu/storage/533php0hjQv7ut-cs-91-127.pdf
Goal
  Formalize a simple GA which is amenable to mathematical analysis.
Preliminary considerations
  lemma1:
  pi(t): proportion of i in the t generation.
  si(t): probabiliy of i that is selected as parents.
  ri,j(k): the probability of reproductive processing base on parents i&j will result k.
  Exp(pk(t+1)) = sum[ij, ](si(t)sj(t)ri,j(k))
  lemma2:
  ri,j(k|l) = ri|k,j|k(l)
  if and only if:cross(i|l, j|l)=>k
  cross(i, j)=>k|l
  Theorem 1:
  Matrix with i,j:
  mi,j = ri,j(0)
  Sigmak(s) = s0|k(t) + s1|k(t) .... sl|k(t)
  Exp(pk(t+1)) = sum[ij, ](si(t)sj(t)ri,j(k))
  	       = sum[ij, ](si(t)sj(t)ri|k,j|k(0))
  	       = sum[ij, ](si|k(t)sj|k(t)rij(0))
	       = sum[ij, ]Sigmak(s)Mi,j
  Theorem 2:
  1 = sum[k, ]ri,j(k) = sum[k, ]ri|k,j|k(0)
  The hole matrix is symmetric. ri,j(k) = rj,i(k) and ri,j(k) = r!i,!j(!k)
  The change between generation can be represented by F' matrix multiplication M without resort to any population

# Cellular automaton & Parttern

## Mechanisms of Emergent Computation in Cellular Automata
density classi cationtask: find out the majority of IC
synchronization task: periodic oscillation between all 1/0.

regular domains: homogeneous region of space-time. pattern.
embedded particles: recurrent structure found at domain boundaries.
particle interactions: two or more particles collide.

filtered configuration space-time diagram:
regular domains <==> remaining intradomain
embedded particles <==> wall transistion
condensation time: nondomain/particle, depends on IC
catlog:
1. possible domains/particle type/pairwise particle interactions with probabilities.
2. approximate particle probability distribution at condensation time.
iteratelly process the IC according to the catlog until no particle.

##
https://www.mcgill.ca/mathematical-physiology-lab/files/mathematical-physiology-lab/lg-mcm-1979-nyacademy-sciences.pdf
periodic patterns: periods of apnea alternate with periods of breathing.

