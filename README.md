# Cutting Stock Problem

This project uses a genetic algorithm for Cutting Stock Optimization.

## Introduction

The Cutting Stock Problem is a classic optimization problem where the objective is to determine the most efficient way to cut large rolls of material into smaller pieces to meet specific customer requests while minimizing waste. This implementation utilizes a genetic algorithm to find optimal cutting patterns.

![images](https://github.com/user-attachments/assets/279bb8f3-c203-4c43-830b-3053a07fb74c)

## Genetic Algorithm Overview

A genetic algorithm (GA) is a heuristic search and optimization technique inspired by the process of natural selection and genetics in biological evolution. It is used to find approximate solutions to optimization and search problems, particularly in cases where the solution space is vast and complex.

## Key Concepts of Genetic Algorithms:
- **Population:** A set of potential solutions (called chromosomes or individuals) to the problem. Each individual is typically represented as a string (or array) of genes.
- **Selection:** A process of choosing the fittest individuals from the current population to create offspring for the next generation. The fitter the individual, the higher its chance of being selected.
- **Crossover:** Also known as recombination, crossover is the process of combining two parent solutions to produce new offspring. This mimics the biological process of reproduction and promotes the inheritance of good traits from both parents.
- **Mutation:** A mechanism to introduce randomness by randomly altering genes in an individual’s chromosome. Mutation ensures genetic diversity and helps the algorithm avoid local optima.
- **Fitness Function:** A function that evaluates how well an individual solves the problem at hand. The fitness score determines the probability of an individual being selected for reproduction.
- **Generations:** The algorithm evolves through generations, each time producing a new population of individuals. Over successive generations, the population "evolves" towards better solutions.

## Advantages of Genetic Algorithms:
- **Global Search:** GA explores a wide solution space, making it effective for finding global optima in complex problems.
- **Adaptability:** GA can handle a variety of problems, including those with non-linear, non-differentiable, or highly constrained solution spaces.
- **Parallelism:** The population-based approach allows multiple solutions to be explored simultaneously, speeding up the search process.

## Implementation Details

1. **Initialization**: 
   - The main class is initialized with several parameters: 
     - `maximum_iterations`: The maximum number of iterations for the algorithm.
     - `num_of_population`: The number of individuals in the population.
     - `randomness`: The probability of mutation.

2. **Input Function**: 
   - This function takes a file path as input and reads the data from the specified file. The data includes:
     - The length of the rolls.
     - A list of requests for smaller pieces.
     - The expected number of rolls needed.
   - This data is stored in instance variables for later use.

3. **Creating the Initial Population**: 
   - The `create_population` function generates an initial population of chromosomes, where each chromosome is a random permutation of the indices representing the requests.

4. **Fitness Function**: 
   - The `fitness_function` calculates the fitness of each chromosome. The fitness is defined as the number of rolls required to fulfill all requests represented in the chromosome. 
   - The function iterates over the requests, keeping track of the current sum of pieces. If the sum exceeds the length of a roll, a new roll is initiated.

5. **Initial Fitness Calculation**: 
   - The `initial_fitness_of_each_chromosome` function calculates the fitness for each chromosome in the initial population and returns a list of fitness values.

6. **Finding Minimum Fitness**: 
   - The `min_fitness` function identifies the chromosome with the minimum fitness value in the current population, returning both the fitness value and the index of the chromosome.

7. **Generating New Generations**: 
   - The `create_new_generation` function generates a new generation of chromosomes through selection, crossover, and mutation. It randomly selects a subset of chromosomes from the current population, identifies the best chromosomes within that subset, and uses them as parents to create a new child chromosome. 
   - This child chromosome undergoes mutation based on a certain probability, and the process repeats until the desired number of new chromosomes is generated.

8. **Creating New Children**: 
   - The `create_new_child` function performs crossover between two parent chromosomes to create a new child chromosome. It randomly selects a section from the parent chromosomes and copies that section to the child. The remaining positions are filled with the remaining requests in the order they appear in the other parent chromosome.

9. **Applying Mutation**: 
   - The `create_mutation` function applies mutation to a chromosome by randomly selecting two positions and swapping the values at those positions with a certain probability.

10. **Running the Algorithm**: 
    - The `run` function serves as the main loop of the genetic algorithm, iteratively creating new generations until either the maximum number of iterations is reached or the fitness of the best chromosome improves. 
    - In each iteration, it creates a new generation, evaluates the fitness of the new generation, and updates the current best solution if a better one is found.
