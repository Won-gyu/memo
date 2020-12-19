By amit

A* is basically an informed variation of Dijkstra.
A* is considered a "best first search" because it greedily chooses which vertex to explore next, according to the value of f(v) [f(v) = h(v) + g(v)] - where h is the heuristic and g is the cost so far.

Note that if you use a non informative heuristic function: h(v) = 0 for each v: you get that A* chooses which vertex to develop next according to the "so far cost" (g(v)) only, same as Dijkstra's algorithm - so if h(v) = 0, A* defaults to Dijkstra's Algorithm.

[source](https://stackoverflow.com/questions/13031462/difference-and-advantages-between-dijkstra-a-star)