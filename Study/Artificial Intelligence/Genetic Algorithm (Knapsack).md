Come under Evolutionary Algorithms. Transforms the NP problem to a Polynomial time problem.
It uses a population of possible solutions in this case it would be the possible items to be put in the knapsack. Each member of the population has a genome encoding (binary encoding).

1. First thing we do is take the entire species randoml,1 in the beginning of the genome means that the item should be included in the bag pack and 0 means otherwise.
2. Next thing we do is the natural selection, now this is done using the fitness function. 'fitness( )' So we see if the sum of the items come under the capacity or not. If not then fitness is 0
3. Then we crossover two parents and create a new generation by random methods of crossover. Repeat the process of natural selection.
4. Then we do a step known as elitism. Where the n number of solution of one generation is simply carried to the next generation.
5. then we do mutation, just randomly change a bit of the genome of a given generation.
This algorithm 
