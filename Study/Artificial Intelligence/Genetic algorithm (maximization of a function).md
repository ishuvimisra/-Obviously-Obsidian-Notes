Ex: (Select Encoding Technique)
   
   $maximum value = 31,  minimum value = 0$
   $population size = 4$
 randomly 4 values are selected 
   

| string number | initial population (random) | X value | fitness f(x) = x^2 | prob = f(x)/sumf(x) | %prob | expected count = f(x)/avg f(x) | actual count(round off exp count) |
| ------------- | --------------------------- | ------- | ------------------ | ------------------- | ----- | ------------------------------ | --------------------------------- |
| 1             | 01100                       | 12      | 144                | 144/1155 = 0.12     | 12.4  | 144/288.75 = 0.49              | 1 (1 time selected)               |
| 2             | 11001                       | 25      | 625                | 0.54                | 54    | 2.16                           | 2                                 |
| 3             | 00101                       | 5       | 25                 | 0.02                | 2.16  | 0.08                           | 0 (wont be selected)              |
| 4             | 10011                       | 19      | 181                | 0.31                | 31    | 1.25                           | 1                                 |
| sum           |                             |         | 1155               | 1                   | 100   | 4                              | 4                                 |
| average       |                             |         | 288.75             | 0.25                | 25    | 1                              | 1                                 |
| maximum       |                             |         | 625                | 0.54                | 54    | 2.16                           | 2                                 |

   
   Select Mating pool where now the population has 01100 1 time,11001 2 times, 1001