[![Open in Visual Studio Code](https://classroom.github.com/assets/open-in-vscode-718a45dd9cf7e7f842a935f5ebbe5719a5e09af4491e668f4dbf3b35d5cca122.svg)](https://classroom.github.com/online_ide?assignment_repo_id=11730543&assignment_repo_type=AssignmentRepo)
# Traveling Salesperson Problem -- Empirical Analysis

For this exercise, you'll need to take the code from the TSP Held-Karp and TSP
Local Search exercises. This can be your own implementation or somebody else's.
You will now do an empirical analysis of the implementations, comparing their
performance. Both the Held-Karp and the Local Search algorithms solve the same
problem, but they do so in completely different ways. This results in different
solutions, and in different times required to get to the solution.

Investigate the implementations' empirical time complexity, i.e. how the runtime
increases as the input size increases. *Measure* this time by running the code
instead of reasoning from the asymptotic complexity (this is the empirical
part). Create inputs of different sizes and plot how the runtime scales (input
size on the $x$ axis, time on the $y$ axis). Your largest input should have a
runtime of *at least* an hour. The input size that gets you to an hour will
probably not be the same for the Held-Karp and Local Search implementations.

In addition to the measured runtime, plot the tour lengths obtained by both
implementations on the same input distance matrices. The length of the tour that
Held-Karp found should always be less than or equal to the tour length that
Local Search found. Why is this?

Add the code to run your experiments, graphs, and an explanation of what you did
to this markdown file.

# Answer

To analyse these two TSP algorithms, I first timed them as they ran with various input sizes.  Here is a table of three random runs with the same inputs for each run:

| Input Size | Method | Results | Run 1 | Run 2 | Run 3 | Median Time |
| :--------: | ------ | ------- | ----- | ----- | ----- | ------------ |
| 1 | Held-Karp | 0, 0, 0 | 0.331ms | 0.268ms | 0.332ms | 0.331ms |
| 1 | Local Search | 0, 0, 0 | 0.095ms | 0.077ms | 0.095ms | 0.095ms |
| 3 | Held-Karp | 3, 3, 3 | 0.168ms | 0.191ms | 0.152ms | 0.168ms |
| 3 | Local Search | 3, 3, 3 | 0.161ms | 0.219ms | 0.181ms | 0.181ms |
| 5 | Held-Karp | 13, 13, 13 | 0.217ms | 0.158ms | 0.161ms | 0.161ms |
| 5 | Local Search | 15, 13, 13 | 0.063ms | 0.049ms | 0.14ms | 0.063ms |
| 10 | Held-Karp | 201, 201, 201 | 17.422ms | 12.309ms | 12.991ms | 12.991ms |
| 10 | Local Search | 218, 218, 201 | 0.242ms | 0.259ms | 0.226ms | 0.242ms |
| 15 | Held-Karp | 262, 262, 262 | 745.638ms | 781.183ms | 777.991ms | 777.991ms |
| 15 | Local Search | 268, 262, 276 | 0.548ms | 0.66ms | 0.423ms | 0.548ms |
| 17 | Held-Karp | 1564, 1564, 1564 | 4.572s | 4.665s | 4.599s | 4.599s |
| 17 | Local Search | 1564, 1617, 1574 | 1.884ms | 0.729ms | 0.635ms | 0.729ms |
| 18 | Held-Karp | 501, 501, 501 | 11.079s | 11.028s | 11.169s | 11.079s |
| 18 | Local Search | 537, 530, 519 | 0.77ms | 0.963ms | 1.263ms | 0.963ms |
| 19 | Held-Karp | 516, 516, 516 | 26.245s | 26.104s | 26.110s | 26.110s |
| 19 | Local Search | 593, 557, 559 | 1.767ms | 1.351ms | 1.434ms | 1.434ms |
| 20 | Held-Karp | DNF after 10 hours |  |  |  |  |
| 20 | Local Search | 566, 543, 584 | 0.741ms | 2.785ms | 1.189ms | 1.189ms |

## Held-Karp Graph:

![Held-Karp Graph](https://github.com/COSC3020/tsp-comparison-Countmooshroom/blob/main/Held-Karp.png?raw=true)

## Local Search Graph:

![Local Search Graph](https://github.com/COSC3020/tsp-comparison-Countmooshroom/blob/main/Local%20Search.png?raw=true)

## Both Data Sets Together:

### Key:

Orange is the Held-Karp algorithm

Purple is the Local Search algorithm

![Local Search Graph](https://github.com/COSC3020/tsp-comparison-Countmooshroom/blob/main/Both%20Graphs.png?raw=true)

Overall, the Held-Karp algorithm has a much higher increase in time as the input size was larger.  On the Held-Karp graph, the time grows very quickly, but on the Local Search graph, the time grows much more slowly (note the scale is also much smaller).  Because of this, the Local Search algorithm is much more efficient.

## Output of Each Algorithm:

### Key:

Orange X's are the Held-Karp algorithm

Purple circles are the Local Search algorithm

![Output Graph](https://github.com/COSC3020/tsp-comparison-Countmooshroom/blob/main/Output%20Graph.png?raw=true)

(note: these points are the average of three outputs from the table at the top)

We should consider the accuracy of the algorithms.  The Held-Karp algorithm always finds the optimal solution, so it is still useful despite it being slower with larger input sizes.  The Local Search algorithm uses a somewhat random system to find the solution, so it often finds an answer that is close to optimal but not quite.  On the graph, you can even see that the Local Search algorithm always produces an output greater than or equal to the Held-Karp algorithm.  Also, the Local Search appears to lose accuracy more as the input size is larger.  Therefore, this algorithm should only be used to quickly find an approximate answer.


