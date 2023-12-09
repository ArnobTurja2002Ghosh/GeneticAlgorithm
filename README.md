# GeneticAlgorithm

## The Main EC Metaphor
<table>
  <tr>
    <th>Problem Solving</th>
    <th>Evolution</th>
  </tr>
  <tr>
    <td>Candidate Solution</td>
    <td>Individual</td>
  </tr>
  <tr>
    <td>Quality</td>
    <td>Fitness</td>
  </tr>
</table>
<ul>
<li> Quality = chance for seeding new solution </li>
<li> Fitness = chance of survival / reproduction </li>
</ul>

## Survivor Selection

● Also called environmental selection
● Most EA use a fixed population size (settings.populationSize), and need a
way of going from (parents + offspring) to next
generation
● Often Deterministic
● Fitness Based (rank all and select)
● Age Based (prefer offspring) 
~~~
while (nextPopulation.length < settings.populationSize){
        let parent1 = RouletteWheelSelection(population, fitnessSum);
        let parent2 = RouletteWheelSelection(population, fitnessSum);
        let child1  = CrossOver(parent1, parent2, settings);
        let child2  = CrossOver(parent2, parent1, settings);
        MutateIndividual(child1, settings);
        MutateIndividual(child2, settings);
    //
    //       Add the children to the population
        nextPopulation.push(child1);
        if(nextPopulation.length<settings.populationSize){
            nextPopulation.push(child2);
        }
    //       Be careful not to add child2 if it would go above the population size
    }
~~~
● Elitism (best n always live)
~~~
for(let i=0; i<numElite; i++){
        nextPopulation.push(population[i]);
    }
~~~

## Variation Operators
Usually divided into two types according to their
number of inputs:
<ul>
<li> Mutation Operator (1 input) </li>
<li> Recombination Operator (> 1 input) 
<li> 2 Inputs = Crossover </li> </li>
</ul>
